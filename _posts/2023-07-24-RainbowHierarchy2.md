---
layout: post
title:  RainbowHierarchy2 사용방법
date:   2023-06-16
image: Unity/RainbowHierarchy2/rainbow.jpeg
tags: Unity
sitemap:
  changefreq: daily
  priority : 1.0
---



---
# RainbowHierarchy2 설명 및 사용 방법
---

## 01.소개

레인보우 시리즈 중 하나인 RainbowHierarchy2입니다.
Hierarchy창의 색상이나, 아이콘의 변경하는 에셋입니다. 이에셋의 장점은 주요사용하는 Player라거나, maincamera등의 색상이나, 아이콘 변경을 해두면 금방금방 오브젝트를 찾을수 있습니다.

그외에도 내가 작업하고 있는 오브젝트에만 백그라운드색을 주고 작업이후에 백그라운드를 제거하는 방법등이 있습니다. 많은오브젝트를 정리하고 관리하기 위한 필수적인 에셋이 아닌가 싶습니다.

[RainbowHierarchy2 에셋스토어](https://assetstore.unity.com/packages/tools/utilities/rainbow-hierarchy-2-106670)
<br><br>

## 2.사용방법

패키지매니저를 통해 RainbowHierarchy2를 프로젝트에 import하셨다면, 바로 사용 할 수 있습니다.
색상이나 아이콘을 변경하고 싶은 Hierarchy창내의 오브젝트를 

**윈도우**의 경우 : <mark style='background-color: #dcffe4'>Alt</mark> + 마우스 좌클릭<br>
**맥**의 경우 : <mark style='background-color: #dcffe4'>Option</mark> + 마우스 좌클릭

합니다.

클릭을 하시면 아래와 같은 창이 생성됩니다.

![01]({{ site.baseurl }}/images/Unity/RainbowFolder/01.png )

위에서 부터 하나하나 설명 해드리겠습니다.

**Object** : 지금 설정하고 있는 오브젝트를 알려줍니다. 클릭하면 오브젝트명으로 변경할수 있습니다.

**Priority** : 적용우선순위입니다. 사실 최상위 오브젝트에는 상관없지만, 하위 오브젝트의 경우 설정해 주어야할 경우가 있습니다. 상위 오브젝트의 설정과 현재 오브젝트의 설정이 다른경우, 우선순위를 통해 상위 오브젝트의 방식을 적용할지, 따로 설정한 세팅을 적용할지 결정합니다.

![02]({{ site.baseurl }}/images/Unity/RainbowFolder/02.png )

**Icon**: 어떤 아이콘으로 변경할지 예시가 보입니다. 원하는 오브젝트 아이콘을 선택해주면됩니다. 

![04]({{ site.baseurl }}/images/Unity/RainbowFolder/04.png )

Icon 내부 **Custom** :  원하는 커스텀 이미지를 오브젝트 Icon으로 사용할수 있습니다.

![02]({{ site.baseurl }}/images/Unity/RainbowFolder/02.png )

**BackGround** : 백그라운드의 경우 오브젝트에 있는 글자의 백그라운드 색상을 의미합니다. 원하는 글자의 백그라운드 색상을 선택하시면 됩니다.

![03]({{ site.baseurl }}/images/Unity/RainbowFolder/03.png )

BackGround 내부 **Custom** : 글자 백그라운드에 이미지를 사용할수있습니다. 원하는 이미지를 글자뒤에 배치해서 사용 할 수 있습니다.

![05]({{ site.baseurl }}/images/Unity/RainbowFolder/04.png )
![06]({{ site.baseurl }}/images/Unity/RainbowFolder/06.png )
이렇게 한눈에 보기편하거나, 원하는 방식으로  오브젝트를 꾸밀수 있습니다. 또한 Hierarchy에 RainbowHierarchyRuleset이 생성됩니다. 이는 Hierarchy 내에서 RainbowHierarchy2로 바뀐 오브젝트의 설정이 모여있습니다.

![08]({{ site.baseurl }}/images/Unity/RainbowFolder/08.png )

세부 사항에 대해서도 설명해 드리겠습니다.
**Recursive**의 경우, 현재 오브젝트의 하위 오브젝트에도 적용여부입니다. 마치 상속처럼 적용을하고 싶다면 Check를 해주시면되고, 이렇게 적용시키고도 몇개의 하위 오브젝트는 자체적인 방식을 사용해야한다면 위에서 설명해드린, Priority를 통해 우선순위를 적용해주면됩니다.

![07]({{ site.baseurl }}/images/Unity/RainbowFolder/07.png )
![06]({{ site.baseurl }}/images/Unity/RainbowFolder/06.png )
**톱니바퀴**의 경우 누르게 되면 아래 이미지 같이, 인스펙터창에서 레인보우히키라키가 적용된 모든 오브젝트를 보여줍니다. 간편하게 설정을 수정 할수 있습니다.

**가운데아이콘**의 경우 누르게되면 현재 이설정이 적용된 오브젝트만 보여줍니다.

**X**아이콘의 경우 누르게도면, 현재 설정한 모든설정이 초기화됩니다.

RainbowHierarchy2의 경우 RainbowFolder처럼 편리함을 주는 에셋입니다. 개인적으로 오브젝트가 늘어날수록 상위오브젝트로 이름을 정하고 하위오브젝트들을 모아주지만, 그렇게 하더라도 숫자가 많아지면 구분하고 관리하기 힘들게됩니다. 이런경우 정말 좋은 해결 방법입니다. 사실 대응되는 무료에셋이나 깃에서 공유되는 무료에셋으로 대처가 가능한것은 사실입니다. 