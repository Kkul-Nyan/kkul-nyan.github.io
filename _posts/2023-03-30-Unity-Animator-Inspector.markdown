---
layout: post
title:  Unity 애니메이터 인스팩터창
date:   2023-03-30
image: Unity/cat004.webp
tags: ["Unity"]
---

---
## Unity 애니메이터 인스팩터창
---

![Example]({{ site.baseurl }}/images/UnityAnimator/01.webp )

**1.Controller** : Asset에 만든 Animator Controller를 추가하여 Animator를 정리 및 관리

**2.Avater** : 캐릭터의 아바타인데, 핵심은 아바타를 움직임의 기초가 되는 뼈대 정보

**3.Apply Root Motion** : Animator를 가진 객체의 위치(position)와 회전(rotation)을 애니메이터자체에서 관리할지 여부. 간단히 비체크시 걷는 애니메이션이 작동해도 제자리에서 움직이지만, 체크시 걷는 애니메이션이 작동시 위치값이 변해서 캐릭터가 이동하게된다. 스크립트로 조작하는 캐릭터의 움직임을 이상하게 만들수도있다.


**4.UpdateMode** : 간단히 스크립트에서도 Time.deltaTime같이  TimeScale을 조정하는 부분이 있는것과 같은 목적이다. 
   - 1.Normal :  Update와 싱크되어 애니메이터 재생속도를 TimeScale과 일치시킨다.
   - 2.Animate Physics : FixedUpdate와 싱크되어 작동한다. FiexedUpdate가 물리효과를 가진 오브젝트를 조정할때 자주사용되는만큼, 역시 물리상호작용을 하는 오브젝트이 모션을 애니메이션화 할경우 사용한다.
   - 3.UnscaledTime : TimeScale없이 애니메이션 그대로의 속도로 재생된다. 


**5.Culling Mode** : 내 카메라 밖에서 보이지 않을 떄 어떻게 작동시킬지이다.
   - 1.Alway Animation : 항상 작동
   - 2.Cull Update Transforms : 2,3번 모두 보이지 않을경우 작동하지 않는것이지만, 2번의 경우는 IK, Transform, 리타켓(리타게팅은 모델의 골격 구조 사이에 연관성을 제공하기 때문에 아바타가 설정된 휴머노이드 모델에만 적용 가능합니다. => 구조상 자식으로 있는 다른캐릭터에도 애니메이터를 돌려씀)이 비활성화된다.
   - 3.2번처럼 일부만 생략되는것이 아니라 전부 비활성화 시킨다.
