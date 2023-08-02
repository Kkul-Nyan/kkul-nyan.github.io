---
layout: post
title:  .?Invoke()
date:   2023-06-09
image: Unity/cat002.jpeg
tags: Unity
---

---
## Unity .?Invoke()
---



.?Invoke는 유니티에서 null을 처리하는 연산자입니다.<
만약 method.?Invoke(); 의 케이스에서 method가 null인 경우,
Invoke는 호출되지 않습니다.

이런 방식을 사용하는 이유는 <mark style='background-color: #dcffe4'>델리게이트 때문입니다.</mark>
델리게이트는 대리자로서 다른 함수를 참조 해오기 위해 사용합니다.


참조해온다는 말은 참조값이 없을수도 있다는 의미입니다.
<mark style='background-color: #dcffe4'>.?Invoke가 없다면 Invoke에서 작동시킬 참조값이 없으므로 Null 오류가 발생</mark>할것입니다
따라서, .?Invoke를 사용함으로서, 델리게이트에서 참조값이 있을경우에만 호출하는
안정적인 스크립트를 작성할수 있게 됩니다.
