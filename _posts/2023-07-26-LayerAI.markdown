---
layout: post
title:  Layer AI 사용방법
date:   2023-07-26
image: Unity/LayerAI/layerAI.webp
tags: ["Unity"]
---



---
# Layer AI 설명 및 사용 방법
---

## 1. 에셋 소개
Layer AI는 요즘 유명한 그림을 그러주는 AI입니다. Layer AI 별도의 홈페이지에서 원하는 그림을 그릴 수도 있지만,
Unity를 통해 간단한 그림을 그릴 수도 있습니다.
구독 방식의 결제 방식을 가지고 있습니다. 사실 기본에서는 정말 간단한 아이콘을 생성해서 사용하는데,
제작 중인 디자인 스타일이 다르면, 유료 결제를 해서 스타일을 사용하거나, 다른 방법을 사용해야 할 것입니다.
그래도 간단한 테스트 프로젝트 제작이나 포트폴리오를 만들 때는 유용합니다.

먼저, 유니티에서 사용방법을 설명하고, 이어서 바로 홈페이지에서 사용하는 방법을 적어두었습니다.

[Layer AI 에셋스토어](https://assetstore.unity.com/packages/tools/generative-ai/layer-ai-257854)<br>
[Layer AI Homepage](https://layer.ai/)
<br><br>

## 2. 세팅 및 사용방법

#### 유니티 세팅 방법
<br>

LayerAI를 유니티에서 사용하기 위해선 에셋을 임포트해 주신 뒤, LayerAI에 회원가입을 진행하고, 토큰을 세팅에 입력해 주면 됩니다.

가장 먼저 패키지 매니저를 통해, Layer AI를 import 해주시면 됩니다.

![01]({{ site.baseurl }}/images/Unity/LayerAI/01.webp)

다음으론, 위 스크린샷처럼 **Window - LayerAI - Setting** 을 눌려주시면 됩니다.
그럼 아래와 같은 창이 뜨게 됩니다.

![02]({{ site.baseurl }}/images/Unity/LayerAI/02.webp)

AccessToken을 입력해야 합니다. 이를 위해서, LayerAI에서 회원가입을 하신 뒤 미리 받아둔 토큰을 넣어주시거나, **Create your acess token**을 클릭하신다면, 토큰 발급 창으로 이동하게 됩니다. 만약 회원가입을 안 하셨다면, 회원가입을 해주셔야 합니다.

![03]({{ site.baseurl }}/images/Unity/LayerAI/03.webp)

**Create your acess token**을 클릭하신 뒤, 회원가입을 하셨다면, 위와 같은
창을 보실 수 있습니다. 노란색으로 표시해둔 Generate new token을 클릭하시면,
토큰 이름을 적는 창이 뜨고, 거기서 원하는 이름을 적어주시면 매우 긴 토큰 값을 줍니다.

그 토큰을 Setting 창에서 넣어주신 뒤 **Save**를 눌려주시면 유니티에서 사용하기 위한 세팅이 완료되었습니다.

#### 사용방법
<br>

유니티 창에서 **Window - LayerAI - Generate Assets**를 클릭해 주시면 아래와 창은 윈도우가 생성됩니다.

![04]({{ site.baseurl }}/images/Unity/LayerAI/04.webp)

무료 사용자라면 기본으로 주어지는 **Style**을 통해 캐릭터인지, UI 인지에 따라 선택해 주시면 됩니다. Style에 따라 생성되는 그림은 매우 다릅니다.

**Prompt**에는 만들고자 하는 그림의 특징들을 적어주시면 됩니다. 그 후 **Forge**를 클릭해 주시면 이미지를 **4장** 생성해 줍니다.

![05]({{ site.baseurl }}/images/Unity/LayerAI/05.webp)

위에 예시는 처음 2번은 Style은 캐릭터, Prompt는 Yellow Cat and cat wear fantasy Armor로 생성한 캐릭터이며, 2번 생성했기에 총 8장이 나왔습니다.

그리고, 다음으론 Style에 UI, Prompt에는 UI button. cyber funk style. edge is gray like iron을 작성하고 UI 버튼 이미지를 생성했습니다.

사실 유니티 자체에서는 정말 간단하게 생성 가능합니다.
좀 더 세부적인 부분을 살리기 위해서는 LayerAI 홈페이지에서 만드는 것이 좋습니다.

Layer AI 홈페이지에 들어가셔서 로그인을 해주신다면, 자동으로 아래와 같은 창으로 들어가시게 됩니다.

![06]({{ site.baseurl }}/images/Unity/LayerAI/06.webp)

스타일 추가는 유료 구독을 하셔야지 가능합니다. 무료에서는 사용이 안 됩니다.

유료 구독체계는 아례 스크린샷과 같습니다.

![07]({{ site.baseurl }}/images/Unity/LayerAI/07.webp)

![08]({{ site.baseurl }}/images/Unity/LayerAI/08.webp)

이미지를 생성하기 위해선 로그인 시 들어온 창에서 **Asset Studio**를 눌려주시면 됩니다.

![09]({{ site.baseurl }}/images/Unity/LayerAI/09.webp)

기본적인 사용방법은 유니티에서 사용하는것과 동일합니다.
오른쪽 Canvas에서 원하는 Style과 Prompt를 작성한뒤 Forge를 클릭했을 때, 이미지를 4장 생성합니다.

하지만 여기서는 **Resolution**을 통해 원하는 해상도를 선택 가능하며, 왼쪽 부분을 보시면 그림판 처럼 간단히 그림을 그릴수 있게되어있습니다. 아래스크린샷 처럼 간단하게 그림을 그린뒤 Style과 Prompt를 적고 생성해주시면, 간단히 그린 그림을 기준으로 생성되게됩니다. 

![10]({{ site.baseurl }}/images/Unity/LayerAI/10.webp)

이렇게 생성된 그림 중 원하는 그림을 클릭 시 자동으로 변경됩니다.
선택한 그림의 디테일을 살리거나, 좀 더 원하는 부분이 있다면,
**올가미**를 통해 세부사항을 살릴 수 있습니다.

![11]({{ site.baseurl }}/images/Unity/LayerAI/11.webp)

**올가미**로 잡고 그 부분에 빨간 점을 찍었습니다. Close 버튼 느낌이 있었으면 좋을 거 같아서 찍어준 뒤 다시 Forge를 시키면, 위 스크린샷처럼, 그 부분만 생성해서 보여준 뒤 선택을 하게 되면, 그 부분만 교체된 걸 확인할 수 있습니다.

이렇게 만든 그림을 유니티로 다운로드하기 위해선, 오른쪽 하단의 **Export Asset** 눌려주시면 아래와 같은 창이 뜨게 됩니다.
원하는 저장 위치를 선택해 주시면, 사이트 내에 저장되게 됩니다.

![12]({{ site.baseurl }}/images/Unity/LayerAI/12.webp)

그럼 왼쪽 상단의 버튼을 눌려주시면 아래와 같은 메뉴가 뜨게 됩니다.
이중 표시해 준 **Your Drive**를 클릭해 주시면, 저장된 에셋을 보실 수 있습니다.

![13]({{ site.baseurl }}/images/Unity/LayerAI/13.webp)

저장하고자 하는 에셋을 우클릭하시면 다운로드 할 수 있습니다.

아래 사진은 제가 생성한 2개의 이미지입니다.
이렇게 간단하게 수정까지 하면서 원하는 이미지를 생성할 수 있습니다.
좀 더 다양한 스타일과 내가 원하는 느낌의 이미지를 생성하기 원한다면 유료 구독을 해야겠지만, 기본적인 스타일로도 충분히 사용하기 좋은 에셋입니다.

![15]({{ site.baseurl }}/images/Unity/LayerAI/15.webp)

![16]({{ site.baseurl }}/images/Unity/LayerAI/16.webp)