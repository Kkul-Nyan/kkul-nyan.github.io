---
layout: post
title:  C# 백준 3003
date:   2022-08-29
image: C.webp
tags: [C#, 백준]
---

---
## 백준 입출력과사칙연산 3003
---


```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 3003
    {
        static void Main(string[] args)
        {
            string[] num = Console.ReadLine().Split();
            int[] nums = new int[num.Count()];
            int[] basenum = { 1, 1, 2, 2, 2, 8 };

            for(int i =0; i< num.Count(); i++)
            {
                nums[i] = basenum[i] - int.Parse(num[i]);
                Console.Write(nums[i] + " ");
            }
        }
    }
}
```

<mark style='background-color: #dcffe4'> string[] num </mark> 를 통해 입력값을 받아줍니다.  
<mark style='background-color: #dcffe4'> int[] nums</mark> 를 통해 출력값을 받아줄 int 집합을 선언해둡니다.
<mark style='background-color: #dcffe4'> int[] basenum</mark>를 통해 주어진 계산을 위한 변수값을 모아줍니다.
<br><br>
각 집합으로 역할에 맞게 변수를 배분해주었습니다.  
하나 하나식을 만들어 계산하지 않고, **반복문**을 통해 한번에 계산해주겠습니다.
<br><br>
<mark style='background-color: #dcffe4'> for</mark>를 통해 반복문을 선언 해준뒤, 선언해둔 집합은 0부터 시작이므로<br> 
i = 0부터 시작해서 <mark style='background-color: #dcffe4'>num.Count()</mark>를 통해 집합안의 갯수만큼 반복해주겠습니다  
<mark style='background-color: #dcffe4'> basenum[i]</mark>에 입력값을 빼서 출력해줄갑을 받은뒤,  
<mark style='background-color: #dcffe4'> Console.Write()</mark>를 통해 바로바로 백준에서 제시한 형식으로 출력해줍니다.<br>
<mark style='background-color: #dcffe4'> WriteLine()</mark>가 아닌 <mark style='background-color: #dcffe4'>Write()</mark>를 사용한 이유는 제시한 형태에 맞춰주기 위해서입니다.

