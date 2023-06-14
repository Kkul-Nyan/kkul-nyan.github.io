---
layout: post
title:  Unity ScriptableObject 사용방법
date:   2023-06-13
description: about Unity ScriptableObject
image: unity.jpeg
tags: Unity
sitemap:
  changefreq: daily
  priority : 1.0
---
---


---
## Unity ScriptableObject 설명 및 작성방법
---


![]({{ site.baseurl }}/images/20230613/03.png )

```c#
using UnityEngine;
using Sirenix.OdinOdinInspector;

[CreateAssetMenu(fileName = "ItemData", menuName = "New ItemData")]
public class ItemData : ScriptableObject
{
  [ShowInInspector]
  private int id = 0;
  public int ID{
    Get{
      return id;
    }
  }
   
}
```

1. <mark style='background-color: #dcffe4'>UnityEditorScriptableObject</mark>는 기존 클래스와 다르게 데이터를 저장할수 있는 대용량 데이터 컨테이너입니다.

2. 굳이 기존 class 대신 사용하는 이유는 프리팹을 생성할때마다 사본을 계속생성합니다. 즉, 중복되는 데이터가 인스턴스를 생성할수록 계속 생성되게 됩니다. 그러나 ScriptableObject를 이용해서 데이터를 저장한후, 인스턴스로 생선되 프리팹에서 값을 참조하게되면, <mark style='background-color: #dcffe4'>사본을 계속 생성하지 않고, 메모리에 단 하나의 사본만 생성해서 사용합니다.</mark>

3. 메모리상 이점뿐만 아니라, 데이터관리에서도 이점이있습니다. 예를들어, "검"이라는 근접무기를 구성한다면, 인벤토리에 쓰일 "검", 몬스터를 죽이거나 제작해서 바닥에 드랍되는 "검", 플레이어 Object가 장착하고 있는 "검" 등 하나의 대상이지만 구성하는 스크립트가 다르고 용도가 다른 프리팹들이 여러개 나오게 되는경우도 있습니다. 이때 <mark style='background-color: #dcffe4'>ScriptableObject를 통해 하나의 데이터에셋에 모아두고 손쉽게 여러 프리팹을 관리</mark>할수있습니다.

4. ScriptableObject 사용시 MonoBehaviour 대신 ScriptableObject를 선언해줍니다. 다음으로 class위에 [CreateAssetMenu(fileName = "ItemData", menuName = "New ItemData")]를 작성합니다 이는 Create Asset에서 사용할 메뉴를 만드는 부분입니다. fileName의 경우, 에셋생성이 기본 에셋이름값입니다. 다음으로 menuName의 경우 Create에서 사용할 메뉴 이름입니다.

5. ScriptableObject 사용시 주의할 부분이 있습니다. 런타임에서 Update로 데이터값이 변경되면, <mark style='background-color: #dcffe4'>런타임이끝나더라도 원래값이 아니라 런타임중에 변경된 값이 보관되고 있는 경우도 있었습니다.</mark> 따라서, 저는 ScriptableObject 사용할 떄, 외부데이터에 의해 오염되는 것을 방지하기 위해 Get을 이용한 읽기전용으로 만들어서 사용하는 경우가 많습니다. 특히, 여러스크립트에서 사용할 초기값을 몽땅 모아두는 역할로 저는 많이 사용하기때문에, 더욱이 데이터 오염에 신경쓰고있습니다.
