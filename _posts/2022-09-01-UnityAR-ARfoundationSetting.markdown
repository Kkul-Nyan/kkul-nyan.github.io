---
layout: post
title:  UnityARFoundation 기본세팅
date:   2022-09-01
image: AR.webp
tags: ["Unity", "AR"]
---

---
### UnityAR기본세팅
---
![ARF1]({{ site.baseurl }}/images/ARFoundation/ARF4(1).webp)
<br><br>
1.가장 먼저 유니티 <mark style='background-color: #dcffe4'>[Window]</mark>탭에서 <mark style='background-color: #dcffe4'>Package Manager</mark>를 열어줍니다
2.<mark style='background-color: #dcffe4'>Package Manager</mark>에서 <mark style='background-color: #dcffe4'>Unity Registry</mark>를 선택해줍니다
  - <mark style='background-color: #dcffe4'>Unity Resistry</mark>는 유니티 기본제공되는 API들입니다.<br>

3.<mark style='background-color: #dcffe4'>AR Foundation, ARCore XR Plugin, ARKit Face Tracking, ARKit XR Plugin</mark>를 설치해줍니다.
  - <mark style='background-color: #dcffe4'>AR Foundation</mark>은 유니티 AR을 사용하기 위해 가장 필수적으로 설치해주어야합니다.
  - <mark style='background-color: #dcffe4'>ARCore</mark>는 AR을 안드로이드 플랫폼에서 사용하기위한 API입니다.
  - <mark style='background-color: #dcffe4'>ARKit</mark> 2종류는 AR을 IOS플랫폼에서 사용하기위한 API입니다.
  - 주의할 점으로, <mark style='background-color: #dcffe4'>AR Foundation</mark>의 버전과 동일한 버전을 설치해주어야합니다.
<br><br>
![ARF2]({{ site.baseurl }}/images/ARFoundation/ARF4(2).webp)

설치가 완료되었으면, <mark style='background-color: #dcffe4'>Hierarchy</mark>화면을 우클릭하여 'XR'에서 <mark style='background-color: #dcffe4'>ARSession</mark>과 <mark style='background-color: #dcffe4'>AR Session Origin</mark>을 생성해줍니다.
  - <mark style='background-color: #dcffe4'>AR Session</mark>은 AR에 관련된 연산을 위해 필요한 오브젝트입니다.
  - <mark style='background-color: #dcffe4'>AR Session Origin</mark>은 카메라와 관련된 부분이 있습니다.
<mark style='background-color: #dcffe4'>AR Session Origin</mark>을 설치해주셨다면, 기존의 카메라를 삭제해주시면됩니다. 
  - <mark style='background-color: #dcffe4'>AR Session Origin</mark>에 있는 카메라가 AR카메라입니다. 기존 생성되어있는 카메라를 삭제하신뒤, <mark style='background-color: #dcffe4'>AR Session Origin</mark> 하위에있는 **AR Camera의 Tag를 MainCamera**로 해주시면됩니다.
<br><br>
![ARF3]({{ site.baseurl }}/images/ARFoundation/ARF4(3).webp)

<mark style='background-color: #dcffe4'>AR Session Origin</mark>의 하위에 있는 AR Camera에서 원하는 방식을 선택해주시면됩니다.<br> inspector창에서 ARCameraManager스크립트를 보시면, FacingDirection이 나타납니다. **World의 경우 후면카메라, User의 경우 전면 카메라**입니다.
<br><br>
이상으로 아주 기본적인 API설치와 기본세팅입니다.