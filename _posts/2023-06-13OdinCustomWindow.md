---
layout: post
read_time: true
show_date: true
title:  Unity 오딘인스팩터 커스텀 윈도우 만들기
date:   2023-06-13
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

![Example](assets/img/posts/20230613/example.gif )

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

1. 가장먼저 UnityEditor를 선언해줘야합니다. 그리고 오딘인스팩터를 사용해서 만들어 줄것이기 때문에, Sirenix.OdinInspector와 Sirenix.OdinInspector.Editor, Sirenix.Utilities.Editor 총 4가지를 선언해주어야합니다.

2. class 선언에서 OdinMenuEditorWindow를 상속 받아줍니다.

3. 가장 기본적으로 작성해야 하는 2가지 메서드는 OpenWindow()와 BuildMenuTree()입니다.

4. OpenWindow()의 경우 유니티 윈도우에서 메뉴를 만들어 줍니다. 위 GIF를 보았을때, Tool에서 DataTable메뉴가 생성되고, 거기에 있는 Item을 클릭하면 윈도우가 열리게 됩니다. 메서드 바로 위의 [MenuItem("Tools/DataTable/Item")]의 경우는 메뉴를 만들 경로 입니다.

![Example](assets/img/posts/20230613/01.png )
5. 