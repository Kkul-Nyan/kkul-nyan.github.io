---
layout: post
title:  RainbowFolder 사용방법
date:   2023-07-24
image: Unity/RainbowFolder/RainbowFolder.webp
tags: ["Unity"]
---



---
# RainbowFolder 설명 및 사용 방법
---

## 01.소개

레인보우 시리즈는 사용 안 해보면 안 한 뒤로 살지만, 한번 사용하면 프로젝트에 꼭 세팅하여 사용하게 되는 유료 에셋입니다.
특히, RainbowsFolder의 경우 프로젝트 창에서 폴더의 색상과 아이콘을 변경할 수 있습니다.
폴더에 다양한 색깔과 아이콘을 사용하여 빠르게 원하는 폴더를 찾을 수 있습니다.
프로젝트 규모가 커질수록 프로젝트 창에 폴더는 늘어나게 됩니다. 많이 사용하는 스크립트 폴더와 일부 폴더에 아이콘을 변경하거나
색상을 변경해둠으로 한눈에 보고 찾을 수 있습니다.

제가 사용하는 다른 방법으로는 저는 빨간색의 폴더의 경우 Git에 공유하지 않는 폴더를 의미합니다.
유료 에셋의 경우, 저작권 등의 문제로 Git에 올리면 문제가 생길 수 있습니다. 따라서 깃이 그 노어를 통해 Git 공유를 방지하는데,
이러한 폴더의 경우 빨간색으로 변경하거나, 빨간색으로 바꾼 폴더에 모아둔 뒤, 구글 드라이브 등 개인 클라우드로 관리합니다.

에셋스토어 링크 : <https://assetstore.unity.com/packages/tools/utilities/rainbow-folders-2-143526>
<br><br>
## 2.사용방법

패키지 매니저를 통해 RainbowFolder를 프로젝트에 import 하셨다면, 바로 사용할 수 있습니다.
색상이나 아이콘을 변경하고 싶은 폴더를

**윈도우**의 경우 : <mark style='background-color: #dcffe4'>Alt</mark> + 마우스 좌클릭<br>
**맥**의 경우 : <mark style='background-color: #dcffe4'>Option</mark> + 마우스 좌클릭

입니다.

클릭을 하시면 아래와 같은 창이 생성됩니다.

![01]({{ site.baseurl }}/images/Unity/RainbowFolder/01.webp )
<br>

위에서부터 하나하나 설명해 드리겠습니다.

**Path** : 말 그래로 폴도의 경로입니다.

**Priority** : 적용 우선순위입니다. 사실 최상위 폴더에는 상관없지만, 하위 폴더의 경우 설정해 주어야 할 경우가 있습니다. 상위 폴더의 설정과 현재 폴더의 설정이 다른 경우, 우선순위를 통해 상위 폴더의 방식을 적용할지, 따로 설정한 세팅을 적용할지 결정합니다.

![03]({{ site.baseurl }}/images/Unity/RainbowFolder/03.webp)

**Icon**: 어떤 아이콘으로 변경할지 예시가 보입니다. 원하는 폴더를 아이콘을 선택해 주면 됩니다.

![03-1]({{ site.baseurl }}/images/Unity/RainbowFolder/03-1.webp )

Icon 내부 **Custom** : 원하는 이미지를 폴더 Icon으로 사용할 수 있습니다. x16의 경우 위 사진에서 좌측 미리 보기를 보시면, 좌하단 Bed를 보시면 이해할 수 있습니다. 폴더 좌하단에 작은 이미지를 생성하는데, 거기에 사용됩니다. x64의 경우 폴더에 사용될 이미지입니다.

![02]({{ site.baseurl }}/images/Unity/RainbowFolder/02.webp )

**BackGround** : 백그라운드의 경우 폴더 하단에 있는 폴더명 글자의 백그라운드 색상을 의미합니다. 원하는 글자의 백그라운드 색상을 선택하시면 됩니다.

![02-1]({{ site.baseurl }}/images/Unity/RainbowFolder/02-1.webp )

BackGround 내부 **Custom** : 글자 백그라운드에 이미지를 사용할 수 있습니다. 원하는 이미지를 글자 뒤에 배치해서 사용할 수 있습니다.

![04]({{ site.baseurl }}/images/Unity/RainbowFolder/04.webp )

이렇게 한눈에 보기 편하거나, 원하는 방식으로 폴더를 꾸밀 수 있습니다. 미리 보기를 통해 어떻게 바뀔지 보고 Apply 혹은 Cancel를 해주시면 됩니다.

![05]({{ site.baseurl }}/images/Unity/RainbowFolder/05.webp )
![06]({{ site.baseurl }}/images/Unity/RainbowFolder/06.webp )

세부 사항에 대해서도 설명해 드리겠습니다.
**Recursive**의 경우, 현재 폴더의 하위 폴더에도 적용 여부입니다. 마치 상속처럼 적용을 하고 싶다면 Check를 해주시면 되고, 이렇게 적용시키고도 몇 개의 하위 폴더는 자체적인 방식을 사용해야 한다면 위에서 설명해 드린, Priority를 통해 우선순위를 적용해 주면 됩니다.

![07]({{ site.baseurl }}/images/Unity/RainbowFolder/07.webp )

**톱니바퀴**의 경우 누르게 되면 아래 이미지같이, 인 스펙터 창에서 RainbowFolder가 적용된 모든 폴더를 보여줍니다. 간편하게 설정을 수정할 수 있습니다.

![10]({{ site.baseurl }}/images/Unity/RainbowFolder/10.webp )

![08]({{ site.baseurl }}/images/Unity/RainbowFolder/08.webp )

이 버튼의 누를 경우, 현재 이 설정을 인스펙터창으로 보여줍니다.

![09]({{ site.baseurl }}/images/Unity/RainbowFolder/09.webp )
이 버튼의 누를경우, 현재 설정된 정보를 초기화합니다. 

RainbowFolder의 경우 정말 한번 사용하면 기본적으로 세팅하게 되는 저렴한 가격에 굉장히 많이 애용하는 에셋입니다.
설정도 간편하고, 관리도 편하기에 사용해 보시는 걸 **추천** 드립니다.


