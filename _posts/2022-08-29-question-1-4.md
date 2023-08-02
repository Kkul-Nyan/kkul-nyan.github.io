---
layout: post
title:  C# 백준 1001
date:   2022-08-29
image: C.webp
tags: [C#, 백준]
---


---
### 백준 입출력과사칙연산 1001
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 1001
    {
        static void Main(string[] args)
        {
            string[] num = Console.ReadLine().Split();
            int A = int.Parse(num[0]);
            int B = int.Parse(num[1]);
            Console.WriteLine(A-B);
        }
    }
}
```

<mark style='background-color: #dcffe4'>string[] num</mark> 으로 글자그룹을 선언 해주고,  
<mark style='background-color: #dcffe4'>Console.ReadLine()</mark>으로 입력값을 받아온뒤 , <mark style='background-color: #dcffe4'>Split()</mark>로 단어 단위로 쪼개어 줍니다.<br><br>
나누어준 <mark style='background-color: #dcffe4'>string</mark>을 <mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 <mark style='background-color: #dcffe4'>string</mark>을 <mark style='background-color: #dcffe4'>int</mark>로 변환해줍니다.

마지막으로, <mark style='background-color: #dcffe4'>Console.WriteLine()</mark>으로 두개의 <mark style='background-color: #dcffe4'>int</mark>의 차이를 출력합니다.
