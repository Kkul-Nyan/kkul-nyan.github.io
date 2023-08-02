---
layout: post
title:  Cinematic Camera 세팅
date:   2023-06-16
image: unity.jpg
tags: Unity
sitemap:
  changefreq: daily
  priority : 1.0
---



---
## Cinematic Camera 세팅 설명 및 작성방법
---

시네머신 카메라에 대해 기본적인 설정 방법을 알려드리겠습니다.<br> 
시네머신 카메라는 스크립트 없이 다양한 스타일의 카메라를 조절할 수도 있으며,<br> 
말 그대로 시네마틱 영상을 만들 때, 손쉽게 만들 수 있게 해줍니다.<br> 

특히, 간단한 설정만으로 다양한 시점을 만들고, 상당히 퀄리티가 좋은 카메라를 완성할 수 있습니다.<br> 

<br>
![01]({{ site.baseurl }}/images/20230616/01.png )
<br>

1. 시네마틱 카메라를 사용하기 위해선 가장 먼저 <mark style='background-color: #ffd700'> PackageManager에서 Cinemachine을 설치</mark>해줍니다.<br> *Cinematic Studio를 설치한다면 다양한 영상과 관련된 패키지를 설치 가능합니다. 이 패키지에 Cinemachine이 포함되어 있습니다.<br>

![02]({{ site.baseurl }}/images/20230616/02.png )

2. 패키지가 추가 되었다면, 이제 씬에 시네머신 카메라를 추가하겠습니다.<br> 히치하이키 창에서 우클릭을 한뒤, Cinemachine에서 다양한 카메라 중 사용할 카메라를 선택해주면 됩니다.<br> 

3. 여기서는 캐릭터를 따라다닐 카메라를 만들것이므로, <mark style='background-color: #ffd700'> Virtual Camera</mark>를 사용하겠습니다.<br> 

![03]({{ site.baseurl }}/images/20230616/03.png )

4. 시네머신 카메라를 추가하면, 바로 카메라가 작동합니다. 단, 작동하지 않을경우 위 스크린샷을 보고 따라해주시면됩니다.
    - 작동하지 않는다는 것은 게임씬이 검은화면으로 변한경우와 기존카메라 시점이 그대로인 경우입니다.<br> 

5. 이런경우, 기존 카메라를 클릭해주신뒤, "AddComponent"를 클릭해서, <mark style='background-color: #ffd700'> CinemachineBrain을 추가</mark>해주시면 됩니다.<br> 자동으로 카메라가 Virtual Camera를 추적하게 됩니다. <br> 

![04]({{ site.baseurl }}/images/20230616/04.png )

6. Virtual Camera가 추적할 대상을 선택해 줍니다.<> 따라다닐 오브젝트를 Follow에 넣어주시면됩니다.<br> 다음으로 플레이어 캐릭터 하위에 카메라가 따라다닐 중심이 될 좌표를 만들어주기 위해 빈오브젝트인 LookAt을 만들어준뒤, LookAt에 넣어주면됩니다.<br> 

![05]({{ site.baseurl }}/images/20230616/05.gif )

7. 이제 <mark style='background-color: #ffd700'> VirtualCamera가 제공하는 다양한 옵션을 설정</mark>해주시면 됩니다. 저는 3인칭시점을 만들고 싶어서 Body에서 3rdPersonFollow를 선택해주었고 설정을 조정해서 카메라를 원하는 위치에 배치했습니다. 이과정에서 아까 만들어준 빈오브젝트 LookAt을 이용하여, 카메라를 좀더 위쪽으로 옮겨주었습니다.<br> 

8. 이제 시네머신 카메라를 간단하게 설정하는 방법을 알아보았습니다.<br> 다음으로는 시네머신 카메라를 좀더 세부적인 설정 값과 역할을 알아보겠습니다.