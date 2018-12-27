---
layout: post
title:  "Unity中Prefab改动之后的回调"
date:   2018-12-27
excerpt: "Unity-Prefab-Apply-Callback."
tag:
- [Unity]
comments: true
---

由于项目是多语言版本，所以平时Text中都是挂载多语言脚本，然后将值存到语言表中，但是为了防止有时候直接存放了中文忘记提到语言表中，找了一个保存prefab时的回调，用于检测。主要逻辑如下。  


{% highlight csharp %}
using UnityEngine;
using UnityEditor;
using System.Text.RegularExpressions;

/// <summary>
/// 这是更改完prefab之后点击apply之后的回调，用处是删除text中的中文
/// </summary>

[InitializeOnLoad]
public class PrefabExtension {

    static PrefabExtension()
    {
        UnityEditor.PrefabUtility.prefabInstanceUpdated += OnPrefabInstanceUpdate;
    }

    static void OnPrefabInstanceUpdate(GameObject instance)
    {
        GameObject prefab = UnityEditor.PrefabUtility.GetPrefabParent(instance) as GameObject;
        if(prefab)
        {
            bool hasChineseWord = false;

            var txtCompList = prefab.GetComponentsInChildren<UnityEngine.UI.Text>(true);
            if(txtCompList.Length > 0)
            {
                foreach(var textComp in txtCompList)
                {
                    if(Regex.IsMatch(textComp.text, @"[\u4E00-\u9FA5]+$"))
                    {
                        Debug.Log("the value <color=red>" + textComp.text + "</color> has been deleted!!!");
                        textComp.text = "";

                        hasChineseWord = true;
                    }
                }
            }

            if(hasChineseWord)
            {
                EditorUtility.SetDirty(prefab);
                AssetDatabase.SaveAssets();
                AssetDatabase.Refresh();
            }
        }
    }
}
{% endhighlight %} 

