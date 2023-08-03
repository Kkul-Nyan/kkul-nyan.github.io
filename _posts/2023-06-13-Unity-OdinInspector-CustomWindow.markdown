---
layout: post
title:  Unity 오딘인스팩터 커스텀 윈도우 만들기
date:   2023-06-13
image: Odin.webp
tags: ["Unity"]
---

---
## 오딘인스팩터 커스텀윈도우
---



![Exa]({{ site.baseurl }}/images/20230613/example.gif )

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

1. 가장먼저 <mark style='background-color: #dcffe4'>UnityEditor</mark>를 선언해줘야합니다. 그리고 오딘인스팩터를 사용해서 만들어 줄것이기 때문에, <mark style='background-color: #dcffe4'>Sirenix.OdinInspector와 Sirenix.OdinInspector.Editor, Sirenix.Utilities.Editor</mark> 총 4가지를 선언해주어야합니다.

2. class 선언에서 <mark style='background-color: #dcffe4'>OdinMenuEditorWindow를 상속</mark> 받아줍니다.

3. 가장 기본적으로 작성해야 하는 2가지 메서드는 <mark style='background-color: #dcffe4'>OpenWindow()와 BuildMenuTree()</mark>입니다.

4. OpenWindow()의 경우, 유니티 윈도우에서 메뉴를 만들어 줍니다. 위 GIF를 보았을때, Tool에서 DataTable메뉴가 생성되고, 거기에 있는 Item을 클릭하면 윈도우가 열리게 됩니다. 메서드 바로 위의 <mark style='background-color: #dcffe4'>[MenuItem("Tools/DataTable/Item")]</mark>의 경우는 메뉴를 만들 경로 입니다.

![01]({{ site.baseurl }}/images/20230613/01.webp )
5. BuildMenuTree()의 경우, 윈도우창 내부를 작성하는 메서드입니다. 가장 먼저, <mark style='background-color: #dcffe4'>var tree = new OdinMenuTree()</mark>는 윈도우창 내부 트리를 위에 첨부된 사진에서 가장 왼쪽을 구성을 tree라하며, 그 tree를 작성하기위해 선언해주어야합니다. 

5-1. 위의 코드에서 작성된 부분 중 <mark style='background-color: #dcffe4'>Add</mark>는 새로운 창을 tree에 추가해주는 메서드입니다. Create New Item 트리를 만들고, 어떻게 작동할지 CreateNewItemData() 클래스를통해 작성했습니다. 따라서 앞의 String의 경우 tree에서 만들어질 창의 이름 부분이며, 뒤의 메서드의 경우, 작동방식에 대한 메서드입니다.

5-2. <mark style='background-color: #dcffe4'>AddAllAssetsAtPath</mark>의 경우 특정 경로에 있는 특정 컴포넌트를 가진 에셋을 창에 추가하는 메서드입니다. 3가지 변수가 있습니다. 가장 먼저 tree상에 보여줄 창의 이름, 다음으론 에셋이 있는 경로, 마지막으론, 어떤컴포넌트를 가져올지를 typeof()로 선언해줍니다. 위를 예시로 보면 tree에 Item이란 창을 만들고, 이창을 클릭했을경우, Assets/DataAsset/ItemData 경로에 있는 모든 ItemData컴포넌트를 가져와서 추가해줍니다.
 
6. 이렇게 작성된 tree를 리턴해주게되면, 경로상의 메뉴에서 Item메뉴를 클릭시 위와같은 모습을 가진 윈도우창이 열리게됩니다.

![02]({{ site.baseurl }}/images/20230613/02.webp)

7. 이제 Add로 선언해준 CreateNewItemData에 대해 설명해주겠습니다. 여기서 ItemData의 경우, ScriptableObject로 작성된 데이터 에셋입니다. CreateNewItemData는 앞에 말씀드린 ItemData 데이터에셋을 인스턴트를 생성해주는 역활을 합니다. <mark style='background-color: #dcffe4'>에셋이 생성되어 경로에 저장된게 아닙니다. 데이터에셋의 변수를 작성하기 위한 인스턴스를 생성했을 뿐입니다.</mark>

8. <mark style='background-color: #dcffe4'>[InlineEditor(ObjectFieldMode = InlineEditorObjectFieldModes.Hidden)]</mark>의 경우, tree를 클릭했을때, 보이는 오른쪽 내용부분을 작성합니다. 이 예시에서는 바로 직전 메서드에서 생성한 Item데이터에셋의 인스턴스를 가져와서 보여줍니다. 이를 통해, 사용자는 Item데이터에셋의 미리선언된 변수의 내용을 작성할수 있습니다.

9. 마지막으로 CreateNewData의 역활은 앞에 만든 인스턴스를 Item 데이터에셋으로 지정된 경로상에 저장을 해주는 역활입니다. [Button("Add New Item")]을 통해 InlineEditor상에서 버튼을 만들어주어서 사용자가 변수를 작성하고 Add New Item이라 적힌 버튼을 클릭하게 되면 메서드가 작동하면서, 작성된 인스턴스를 데이터에셋을 생성합니다. CreateAsset()의 경우, 2가지 변수가 필요합니다. 첫번째로, 에셋으로 생성할 인스턴스를 지정해줍니다. 다음으론, 에셋이 저장될 경로와 이름과 확장자를 작성합니다. 이후 SaveAssets()으로 CreateAsset() 작성된 에셋을 저장해줍니다.

10. 이후 itemData 인스턴스를 생성해주는 이유는 앞에 <mark style='background-color: #dcffe4'>생성한 에셋을 중복해서 작성할 필요도 없으니 초기화 과정</mark>으로 작성 된 것입니다.

11. 이 과정을 통해 오딘인스팩터를 이용한 유니티 커스텀 윈도우창을 만드는 방법이었습니다. 이를통해 손쉽게 아이탬이나 몬스터 등 데이터를 손쉽게 추가하고 관리하기 편해집니다. 이는 프로그래머뿐만 아니라 기획자 등 다른 팀원들도 손쉽게 데이터를 관리하게 도와줍니다.