---
layout: post
title:  C# 백준 25304
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 25304
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 집합과맵01
    {
        static void Main(string[] args)
        {
            int X = int.Parse(Console.ReadLine());
            int N = int.Parse(Console.ReadLine());

            int[] Sum = new int[N];
            int FinishSum = 0;

            for(int i = 0; i < N; i++)
            {
                string[] Num = Console.ReadLine().Split();
                int a = int.Parse(Num[0]);
                int b = int.Parse(Num[1]);
                Sum[i] = a * b; 
            }

            foreach(int item in Sum)
            {
                FinishSum += item;
            }

            if(X == FinishSum)
            {
                Console.WriteLine("Yes");
            }
            else
            {
                Console.WriteLine("No");
            }

        }
    }
}
```

## 영수증
  - 입력 : 총합금액 X이 주어지고, 총 반복횟수 N, 물건가격 a, 물건갯수 b
  - 조건
    - 1.N번 반복해서 a,b 입력값을 받고 a*b값들을 구한 뒤, 
    - 2.N번 a*b값들을 새로운 총합을 구합니다.
    - 3.새로운 총합과 주어진 총합 X를 비교해서 값이 일치한지 아닌지를 구분합니다.
  - 출력 : 구분에 따라 Yes 혹은 No를 출력합니다.<br><br>

먼저 입력조건에 따라 쓰일 <mark style='background-color: #dcffe4'>int.Parse(Console.ReadLine())</mark>로   
총합과 반복횟수를 정수형으로 변환해서 받아줍니다.

조건에 따라 **반복문 2번과 출력을 위한 조건문 1개**를 사용해줘야 합니다.<br>
반복문에서 새로운 정수집합과 정수형이 필요하니 **미리 선언**해 둡니다(Sum[],FinishSum)

<mark style='background-color: #dcffe4'>for반복문 혹은 while 반복문</mark> 통해 입력값을 N번만큼 받아주고,<br>
바로 <mark style='background-color: #dcffe4'>int a, int b</mark>로 정수형으로 입력값을 변환해줍니다.<br>
a와 b의 곱샘값을 바로 <mark style='background-color: #dcffe4'>Sum[] 정수집합</mark>에 넣어줍니다.<br>
정수집합의 시작은 0부터이므로 i값을 0으로 시작합니다.

<mark style='background-color: #dcffe4'>foreach 반복문</mark>을 통해 금방구한 <mark style='background-color: #dcffe4'>Sum[]정수집합</mark>의 값들을 합해줍니다.

마지막으로, 3번쨰 조건인 **주어진 총합X와 우리가 구한 총합 FinishSum이 일치하는지 확인**해주고,<br>
일치여부에 따라 바로  <mark style='background-color: #dcffe4'>Console.WriteLine()</mark>으로 출력값을 출력해줍니다.
