---
layout: post
title:  C# 백준 10926
date:   2022-08-29
image: C.webp
tags: [C#, 백준]
---

---
### 백준 입출력과사칙연산 10926
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 10926
    {
        static void Main(string[] args)
        {
            string A = Console.ReadLine();

            Console.WriteLine(A+"??!");
        }

    }
}
```

### 입렵값뒤에 지정된 문자열을 배치 하는 문제입니다.

<mark style='background-color: #dcffe4'>string A</mark>를 통해 A라는 문자열을 선언해준뒤,  
<mark style='background-color: #dcffe4'>Console.ReadLine()</mark>을 통해 입력값을 가져옵니다.  
<br>
<mark style='background-color: #dcffe4'>Console.WriteLine()</mark>으로 값을 출력해줍니다.  
출력값에 입렵값을 가지고있는 A와 문자열을 의미하는  <mark style='background-color: #dcffe4'>""</mark>  을 통해  
<span style="color:green">입력값 A와 그뒤에 특정 문자열을 함꼐 출력합니다</span>