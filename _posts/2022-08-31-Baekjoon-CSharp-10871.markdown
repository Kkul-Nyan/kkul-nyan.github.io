---
layout: post
title:  C# 백준 10871
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 10871
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 10871
    {
        static void Main(string[] args)
        {
            string[] str = Console.ReadLine().Split();
            int N =int.Parse(str[0]); int X =int.Parse(str[1]);
            
            string[] chars = Console.ReadLine().Split();
            int[] Nums = new int[N];

            for (int i = 0; i < N; i++)
            {
                Nums[i] = int.Parse(chars[i]);
            }

            for (int i = 0; i < N; i++)
            {
                if (Nums[i] < X)
                {
                    Console.Write(Nums[i]);
                    Console.Write(" ");
                }
            }
        }
    }
}
```

## X보다 작은 수 
  - 반복문과 가정법을 섞은 문제입니다.
  - 입력 : 반복횟수 정수 N과 비교할정수 X가 주어진다. 
  - 조건 : N만큼 반복 하며, X와 다른수를 조건(X보다 작은수)에 따라 비교해줍니다.
  - 출력 : 조건문에따라 걸려진 정답을 출력해줍니다.

먼저 첫번째 입력값을 <mark style='background-color: #dcffe4'> string[] str</mark>으로 받아준뒤 헷갈리지 않게<mark style='background-color: #dcffe4'> N,X로 int.Parse</mark>를 통해 정수형으로 변환해줍니다.
2번째 받을 입력값을 위해  <mark style='background-color: #dcffe4'>string[] chars</mark>로 받아준뒤, 반복횟수를 집합개수로 정수형 집합을 선언해줍니다.

먼저 반복문을 통해 두번쨰 **문자열집합을 정수형 집합**으로 변환해주도록 하겠습니다.

변환된 정수열 집합을 집합갯수 만큼 반복문을 반복해주면서 
<mark style='background-color: #dcffe4'>if문</mark>을 통해 **조건인 X 보다 작은 숫자**만 <mark style='background-color: #dcffe4'>if문</mark>안에 식을 작동하게 해주겠습니다.

if문안의 내부식은 <mark style='background-color: #dcffe4'>Console.Write()</mark>를 통해 한줄에 조건에 맞는 숫자를 출력해 주는것입니다.
