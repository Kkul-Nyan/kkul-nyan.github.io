---
layout: post
title:  HDRP Water Setting
date:   2023-08-24
image: Unity/cat005.webp
tags: ["Unity"]
---



---
# HDRP Water Setting 방법
---

유니티 **2022 HDRP**부터는 유니티에서 기본적인 고품질의 Water를 지원합니다. Ocean 과 River, Pool 3종류를 제공합니다.
3가지 모두 고품질의 HDRP에 어울리는 Water로서 세부적인 세팅 역시 가능합니다.

그러나, 생각보다 아무것도 모르는 상태에서 Water를 히키라이키 창의 생성한다 해서 Water가 바로 작동하는 것은 아니라
지금부터 알려드릴 세팅을 차근히 적용해 주셔야 Water가 씬과 게임씬에 보이게 됩니다.


![HDRPWaterSetting01]({{ site.baseurl }}/images/Unity/HDRPWater/HDRPWaterSetting01.webp)

가장 먼저, 히키라이키 창에서 마우스를 우클릭하신 뒤, Water Surface에서 원하는 Water를 선택해 주시면 됩니다.
Water는 Ocean, River, Pool 3종류입니다. 저는 Ocean을 선택했습니다.

![HDRPWaterSettingProjectSetting01]({{ site.baseurl }}/images/Unity/HDRPWater/HDRPWaterSettingProjectSetting01.webp)

히키라이키 창에 Ocean을 생성했지만, 아무것도 보이지 않습니다. Inspertor 창을 보면, 세팅을 변경해달라 경고가 들어와있습니다.
HDRP 세팅을 변경하기 위해 **Edit - Project Setting** 을 들어가겠습니다.

**Qualitay에서 HDRP**를 선택합니다. 설정 창을 살짝만 내리시면, **Water**가 있습니다. **Enable**을 체크해 주시면 됩니다.
스크립트를 통해 Water를 조정할 예정이면, Script Interactions 역시 체크해 주시면 됩니다.

![HDRPWaterSettingProjectSetting02]({{ site.baseurl }}/images/Unity/HDRPWater/HDRPWaterSettingProjectSetting02.webp)

다음은 **Graphics에서 HDRP Global Setting**을 눌려주신 뒤, **Camera**설정에서 **Rendering**설정 하단에 위치한 **Water**를 활성화해 주셔야 합니다.
마지막으로 한 가지 단계만 더 적용하면 이제 Water가 화면에 표시됩니다.

![HDRPWaterSetting02]({{ site.baseurl }}/images/Unity/HDRPWater/HDRPWaterSetting02.webp)

마지막입니다. 여기서는 2가지 방법이 존재합니다. 내가 특정씬에서만 Water를 사용하겠다 or 내가 전체 모든 씬에서 Water를 사용하겠다에 따라 달라집니다.
먼저 전자의 방법은 히치라이키창에서 **빈 게임오브젝트를 생성하신 뒤, Volume을 생성합니다.** 프로필이 없다면 생성해 주면됩니다. 
이제 **Add Override**를 클릭합니다. **WaterRendering**을 선택해 주신 뒤에 **State**를 활성화하고, **Enable**로 해주시면, 바로 화면에 Water가 나타납니다.

![HDRPWaterSettingProjectSetting03]({{ site.baseurl }}/images/Unity/HDRPWater/HDRPWaterSettingProjectSetting03.webp)

후자의 방법은 기존 **Project Setting**에서 전체 세팅을 변경하는 것입니다. 
**Qualitay에서 HDRP**를 선택합니다. 바로 제일 상단에 위치하는 **Volume Profiles**에서 **Default Volume Profile Setting**에서 **Add Override** 하셔서 **WaterRendering**을 생성해 주시면 됩니다. 이렇게 되면 빠로 Volume을 씬에 추가하지 않더라도 기본적인 세팅에서 **WaterRendering**을 사용하기 때문에 씬에 나타나게 됩니다.

![HDRPWaterSettingFinish]({{ site.baseurl }}/images/Unity/HDRPWater/HDRPWaterSettingFinish.webp)

생성해 주신 Water를 선택하고 Inspector 창에서 세팅을 변경하시면 바로 Water 오브젝트를 보면서 자유롭게 세팅을 하면 됩니다. 
유료 Water 에셋보다는 디테일적인 부분은 조금 떨어지는 부분이 있지만, 
다른 Water 에셋들에 비해 가볍고, 상당히 예쁜 Water를 바로 사용할수 있어 좋습니다.