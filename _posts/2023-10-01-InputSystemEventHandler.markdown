---
layout: post
title:  유니티 Input System 사용(이벤트핸들러)
date:   2023-10-01
image: Unity/cat005.webp
tags: ["Unity"]
---



---
# 유니티 Input System 사용(이벤트핸들러)
---

유니티 Input System을 이용해서 KeyBinding 하는 방법은 여러 방법이 있습니다.
제가 가장 많이 사용하는 방법은 **Player Input을 등록한 다음 Invoke Unity Event에 등록**하는 것입니다.
이는 유니티 버튼에서 스크립트를 등록하는 것처럼 간편하지만, 개인적으로 스크립트의 분량이 늘어날수록 오히려 헷갈리게 느껴졌습니다.

다른 방법으로는 지금 소개해 드릴 **이벤트 핸들러로 등록**하는 방법입니다.
처음에는 살짝 헷갈릴 수도 있지만, 굳이 Player Input을 이용하는 것보다 스크립트에서 바로 작성하고 작동시킬 수 있는 편리함과
개인적으로는 양이 많아져도 정리만 어느 정도 해두면 좀 더 구분하기 편한 부분이 있었습니다.

Invoke Unity Event 방식은 다음 글에서 다루기로 하고,
**지금은 먼저 EventHandler로 등록하는 방법을 다루도록 하겠습니다.**




![InputActionSetting]({{ site.baseurl }}/images/Unity/InputSystem/InputActionSetting.webp)

가장 먼저, Input Action을 생성하여 Move에 관련된 세팅을 해주었습니다. Move는 Pass Through 타입에 Vector2를 사용합니다. 각각 WASD로 움직이도록 했습니다.
Run의 경우, 누르고 있을 때, 캐릭터가 달리도록 만들기 위한 액션입니다. Button 타입입니다. Shift를 누를 시 작동하도록 세팅했습니다.

![MakeInputActionScriptByInputAction]({{ site.baseurl }}/images/Unity/InputSystem/MakeInputActionScriptByInputAction.webp)

생성해둔 InputAction을 클릭하시면 위 스크린샷과 같은 Inspector 창이 보이게 됩니다. 이 중 **Generate C# Class를 클릭**해 주시면,
이 InputAction을 이용한 스크립트가 자동으로 생성됩니다.

이제 이 스크립트를 이용해서 메서드를 작성해 줄 스크립트를 생성해 줍니다.

```c#
using UnityEngine;

using UnityEngine.InputSystem;

public class PlayerMove : MonoBehaviour
{
    //기본 변수
    Rigidbody2D rb;
    float moveSpeed = 3;
    float runSpeed = 5;

    //InputAction에서 move값을 받아줄 Vector2입니다.
    Vector2 movement;

    //InputAction으로 생성된 스크립트 변수입니다.
    TestInput testinput;
 

    private void Awake() {
        //InputAction을 사용하기 위해 만든 스크립트 변수를 초기화 해줍니다.
        testinput = new TestInput();

        rb = GetComponent<Rigidbody2D>();
    }

    private void Start() {
        //메서드를 이벤트핸들러를 통해 InputAction에 등록합니다.
        //이부분은 람다식을 통해 등록했습니다.
        testinput.Move.Run.performed += _ => StartRun();

        //StopRun의 경우 정확히는 StopRun(context)입니다. (context)이 생략되어있습니다.
        testinput.Move.Run.canceled += StopRun;
    }

    // PlayerMove라는 이 스크립트가 활성화 되면, testinput이라는 InputAction과 연동된 스크립트를 초기화하고
    // 미리 지정해준 EventHandler를 등록합니다. 
    // 이 부분이 없다면 작동하지 않습니다.
    private void OnEnable() {
        testinput.Enable();
    }

    // 업데이트를 통해 InputAction에서 지정한 WASD의 값이 입력되면 인식하게됩니다.
    private void Update() {
        TestPInput();
    }

    // 업데이트를 통해 인신되어 전달받은 movement값을 통해 FixedUpdate를 이용해서 움직임을 구현합니다.
    private void FixedUpdate() {
        Move();
    }


    private void StartRun()
    {
        moveSpeed += runSpeed;
    }

    private void StopRun(InputAction.CallbackContext context)
    {
       moveSpeed -= runSpeed;
    }
    //Update를 통해 관리하고있습니다. 입력값이 변경되면, movemet 값도 변경됩니다.
    private void TestPInput()
    {
        movement = testinput.Move.Move.ReadValue<Vector2>();
    }

    private void Move()
    {
        //RigidBody2D를 통해 움직임을 구현합니다. FixedUpdate를 이용하믕로 DeltaTime이 아니라 
        //fixedDeltaTime을 사용합니다.
        rb.MovePosition(rb.position + movement * moveSpeed * Time.fixedDeltaTime);
    }
}
```

**Start()에서 이벤트 핸들러를 등록**하고 있습니다. 방식은 2가지 방식으로 작성했습니다.
두 방식 다 크게 차이는 나지 않습니다
첫 번째의 경우, **람다식**을 이용하여 간편하게 만들어준 방식입니다.

2가지 방식 다 testInput(InputAction을 통해 작성된 스크립트)에 이벤트를 등록해주고 있습니다.
이를 통해 Invoke Unity Event 방식과 다르게 InputAction.CallbackContext context를 통해 context 값을 일일이 지정해 주고
다시 Player Input에 등록해 줄 필요는 없습니다.

![MoveTest]({{ site.baseurl }}/images/Unity/InputSystem/MoveTest.webp)


