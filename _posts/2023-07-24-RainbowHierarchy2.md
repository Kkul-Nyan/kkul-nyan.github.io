---
layout: post
title:  RainbowHierarchy2 사용방법
date:   2023-07-25
image: Unity/RainbowHierarchy2/rainbow.jpeg
tags: Unity
---



---
# RainbowHierarchy2 설명 및 사용 방법
---

## 01.소개

레인보우 시리즈 중 하나인 RainbowHierarchy2입니다.
Hierarchy 창의 색상이나, 아이콘의 변경하는 에셋입니다. 에셋의 장점은 주요 사용하는 Player 라거나, maincamera 등의 색상이나, 아이콘 변경을 해두면 금방금방 오브젝트를 찾을 수 있습니다.

그 외에도 내가 작업하고 있는 오브젝트에만 백그라운드 색을 주고 작업 이후에 백그라운드를 제거하는 방법 등이 있습니다. 많은 오브젝트를 정리하고 관리하기 위한 필수적인 에셋이 아닌가 싶습니다.

[RainbowHierarchy2 에셋스토어](https://assetstore.unity.com/packages/tools/utilities/rainbow-hierarchy-2-106670)
<br><br>

## 2.사용방법

패키지 매니저를 통해 RainbowHierarchy2를 프로젝트에 import 하셨다면, 바로 사용할 수 있습니다.
색상이나 아이콘을 변경하고 싶은 Hierarchy 창 내의 오브젝트를

**윈도우**의 경우 : <mark style='background-color: #dcffe4'>Alt</mark> + 마우스 좌클릭<br>
**맥**의 경우 : <mark style='background-color: #dcffe4'>Option</mark> + 마우스 좌클릭

합니다.

클릭을 하시면 아래와 같은 창이 생성됩니다.

![01]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/01.png )

위에서부터 하나하나 설명해 드리겠습니다.

**Object** : 지금 설정하고 있는 오브젝트를 알려줍니다. 클릭하면 오브젝트 명의로 변경할 수 있습니다.

**Priority** : 적용 우선순위입니다. 사실 최상위 오브젝트에는 상관없지만, 하위 오브젝트의 경우 설정해 주어야 할 경우가 있습니다. 상위 오브젝트의 설정과 현재 오브젝트의 설정이 다른 경우, 우선순위를 통해 상위 오브젝트의 방식을 적용할지, 따로 설정한 세팅을 적용할지 결정합니다.

![02]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/02.png)

**Icon**: 어떤 아이콘으로 변경할지 예시가 보입니다. 원하는 오브젝트 아이콘을 선택해 주면 됩니다.

![04]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/04.png)

Icon 내부 **Custom** : 원하는 커스텀 이미지를 오브젝트 Icon으로 사용할 수 있습니다.

![02]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/02.png )

**BackGround** : 백그라운드의 경우 오브젝트에 있는 글자의 백그라운드 색상을 의미합니다. 원하는 글자의 백그라운드 색상을 선택하시면 됩니다.

![03]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/03.png )

BackGround 내부 **Custom** : 글자 백그라운드에 이미지를 사용할 수 있습니다. 원하는 이미지를 글자 뒤에 배치해서 사용할 수 있습니다.

![05]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/04.png)
![06]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/06.png)
이렇게 한눈에 보기 편하거나, 원하는 방식으로 오브젝트를 꾸밀 수 있습니다. 또한 Hierarchy에 RainbowHierarchyRuleset이 생성됩니다. 이는 Hierarchy 내에서 RainbowHierarchy2로 바뀐 오브젝트의 설정이 모여있습니다.

![08]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/08.png )

세부 사항에 대해서도 설명해 드리겠습니다.
**Recursive**의 경우, 현재 오브젝트의 하위 오브젝트에도 적용 여부입니다. 마치 상속처럼 적용을 하고 싶다면 Check를 해주시면 되고, 이렇게 적용시키고도 몇 개의 하위 오브젝트는 자체적인 방식을 사용해야 한다면 위에서 설명해 드린, Priority를 통해 우선순위를 적용해 주면 됩니다.

![07]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/07.png )
![06]({{ site.baseurl }}/images/Unity/RainbowHierarchy2/06.png )

**톱니바퀴**의 경우 누르게 되면 아래 이미지같이, 인 스펙터 창에서 Rainbow Hierarchy가 적용된 모든 오브젝트를 보여줍니다. 간편하게 설정을 수정할 수 있습니다.

**가운데 아이콘**의 경우 누르게 되면 현재 이 설정이 적용된 오브젝트만 보여줍니다.

**X**아이콘의 경우 누르게 도면, 현재 설정한 모든 설정이 초기화됩니다.

RainbowHierarchy2의 경우 RainbowHierarchy2처럼 편리함을 주는 에셋입니다. 개인적으로 오브젝트가 늘어날수록 상위 오브젝트로 이름을 정하고 하위 오브젝트들을 모아주지만, 그렇게 하더라도 숫자가 많아지면 구분하고 관리하기 힘들게 됩니다. 이런 경우 정말 좋은 해결 방법입니다. 사실 대응되는 무료 에셋이나 깃에서 공유되는 무료 에셋으로 대처가 가능한 것은 사실입니다.