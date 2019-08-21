---
layout: post
title:  "c++自定义内存分配器，即allocator类的自定义"
date:   2019-08-21
excerpt: "c++"
tag:
- [memory]
comments: true
---

# c++自定义内存分配器，即allocator类的自定义。

在c++中，平时对象的产生是通过new关键字来的，而allocator可以把分配内存和调用构造函数初始化分开。而在分配内存这一步，就可以让用户玩一点儿花活了，例如向系统申请一大块内存（malloc），反复使用而不释放，这样至少省下了反复与操作系统交互的那些花销。

想要实现在指定内存块生成对象，c++提供了一种语法：

```c++
new (p) Student();
// p是指向一块内存的指针，例如下边的伪代码
void* p = malloc(sizeof(Student));
Student* s = new (p) Student;
```

[Alloctor的官方文档](https://en.cppreference.com/w/cpp/named_req/Allocator#Allocator_completeness_requirements)，其中明确说明需要提供的方法有a.allocate(n)、a.deallocate(ptr, n)和一些构造函数等等。下面先写一个模版，留个坑以后添上真正的自定义内存块维护。

```c++
template<typename T>
class StdFrameAlloc
{
public:
	typedef T value_type;
	typedef value_type* pointer;
	typedef const value_type* const_pointer;
	typedef value_type& reference;
	typedef const value_type& const_reference;
	typedef std::size_t size_type;
	typedef std::ptrdiff_t difference_type;

	template<class U>
	bool operator==(const StdFrameAlloc<U>&) const noexcept
	{
		return true;
	}

	template<class U>
	bool operator!=(const StdFrameAlloc<U>&) const noexcept
	{
		return false;
	}

	template<class U>
	class rebind
	{
	public:
		typedef StdFrameAlloc<U> other;
	};

	T* allocate(const size_t num) const
	{
		if(num == 0)
		{
			return nullptr;
		}

		if(num > static_cast<size_t>(-1) / sizeof(T))
		{
			return nullptr;
		}

        // 这里的malloc可替换成自己的。
		void* const pv = malloc(num * sizeof(T));
		if(!pv)
		{
			return nullptr;
		}

		return static_cast<T*>(pv);
	}

    // 这里的free可替换成自己的。
	void deallocate(T* p, size_t num) const noexcept
	{
		free((uint8_t*)p);
	}

	size_t max_size() const
	{
		return std::numeric_limits<size_type>::max() / sizeof(T);
	}

	void construct(pointer p, const_reference t)
	{
        //这里就是在指定内存块上创建对象
		new (p) T(t);
	}

	void destroy(pointer p)
	{
		p->~T();
	}

	template<class U, class... Args>
	void construct(U* p, Args&&... args)
	{
		new (p) U(std::forward<Args>(args)...);
	}
};
```

使用的话，指定一些stl的数据结构使用该allocator就行了，例如

```c++
int main()
{
	auto vec = std::vector<int, StdFrameAlloc<int>>();
	vec.push_back(1);

	for(auto i : vec)
	{
		cout << i << endl;
	}

	return 0;
}
```

框架就是这样，是参考的官方文档和bsf的。以后添坑！