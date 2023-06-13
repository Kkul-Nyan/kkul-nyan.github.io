---
layout: post
read_time: true
show_date: true
title:  Unity 오딘인스팩터 커스텀 윈도우 만들기
date:   2023-03-30
description: about Unity Custom Window using Odin Inspector
img: banner/unity.jpeg
tags: [Unity, Odin Inspector]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Unity 오딘인스팩터 커스텀 윈도우 만들기
---

![Example](assets/img/posts/20230613/example.png )

1.Controller : Asset에 만든 Animator Controller를 추가하여 Animator를 정리 및 관리

```c#
using UnityEngine;
using UnityEditor;
using Sirenix.OdinInspector;
using Sirenix.OdinInspector.Editor;
using Sirenix.Utilities.Editor;

public class ItemToolbar : OdinMenuEditorWindow
{
    [MenuItem("Tools/DataTable/Item")]
    private static void OpenWindow(){
        GetWindow<ItemToolbar>().Show();
    }
    protected override OdinMenuTree BuildMenuTree()
    {
        var tree = new OdinMenuTree();

        tree.Add("Create New Item", new CreateNewItemData());
        tree.AddAllAssetsAtPath("Item", "Assets/DataAsset/ItemData", typeof(ItemData));

        return tree;
    }

    public class CreateNewItemData{
        public CreateNewItemData(){
            itemData = ScriptableObject.CreateInstance<ItemData>(); 
            itemData.name = "New ItemData";
        }
        [InlineEditor(ObjectFieldMode = InlineEditorObjectFieldModes.Hidden)]
        public ItemData itemData;

        [Button("Add New Item")]
        private void CreateNewData(){
            AssetDatabase.CreateAsset(itemData, "Assets/DataAsset/ItemData/" + itemData.name + ".asset");
            AssetDatabase.SaveAssets();

            itemData = ScriptableObject.CreateInstance<ItemData>(); 
            itemData.name = "New Item Data";
        }
    }
}
```