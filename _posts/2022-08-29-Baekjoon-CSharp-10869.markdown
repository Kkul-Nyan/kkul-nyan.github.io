---
layout: post
title:  C# 백준 10869
date:   2022-08-29
image: C.webp
tags: [C#, 백준]
---

---
### 백준 입출력과사칙연산 10869
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 10869
    {
        static void Main(string[] args)
        {
            string[] n = Console.ReadLine().Split();
            int A = int.Parse(n[0]);
            int B = int.Parse(n[1]);

            Console.WriteLine(A+B);
            Console.WriteLine(A-B);
            Console.WriteLine(A*B);
            Console.WriteLine(A/B);
            Console.WriteLine(A%B);
        }
    }
}
```

사칙연산 전체를 물어보는 문제입니다.

<mark style='background-color: #dcffe4'>string[] num</mark> 으로 글자그룹을 선언 해주고,  
<mark style='background-color: #dcffe4'>Console.ReadLine()</mark>으로 입력값을 받아온뒤 , <mark style='background-color: #dcffe4'>Split()</mark>로 단어 단위로 쪼개어 줍니다.<br><br>
나누어준 <mark style='background-color: #dcffe4'>string</mark>을 <mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 <mark style='background-color: #dcffe4'>string</mark>을 <mark style='background-color: #dcffe4'>int</mark>로 변환해줍니다.

마지막으로, <mark style='background-color: #dcffe4'>Console.WriteLine()</mark>으로  두개의 <mark style='background-color: #dcffe4'>int</mark>의 각각 덧샘,빼기,곱샘,나눗샘, 나누기연산(나머지값) 값을 출력합니다.