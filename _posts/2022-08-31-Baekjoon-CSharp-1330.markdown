---
layout: post
title:  C# 백준 1330
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 조건문 1330
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 1330
    {
        static void Main(string[] args)
        {
            string[] Num = Console.ReadLine().Split();
            int A = int.Parse(Num[0]);
            int B = int.Parse(Num[1]);

            if (A > B)
            {
                Console.WriteLine(">");
            }
            else if (A < B)
            {
                Console.WriteLine("<");
            }
            else
            {
                Console.WriteLine("==");
            }

        }
    }
}
```

## 먼저 입력 조건과 출력 조건을 확인하겠습니다.
  - 입력 : A, B 2개의 숫자가 주어진다
  - 출력 : A,B를 비교해서 <,>,== 을 출시한다
<br><br>
2개의 숫자가 연달아 주어 지므로 <mark style='background-color: #dcffe4'> string[]</mark>로 입력받는 문자열을 집합으로 받아주고, <br> 바로 <mark style='background-color: #dcffe4'>Split()</mark> 으로 각각 분리해줍니다.<br>
문자열형으로 받은 입력 값을 각각 <mark style='background-color: #dcffe4'>int.Parse</mark> 를 통해 정수형으로 변경해줍니다.
<br><br>
입력 받은 값을 출력조건에 맞추어서 가공합니다.
<br> 가정법 if, swich 중 전 if가정법을 사용할것입니다.
<br> 3가지 중 하나가 정해진 조건에 따라 나와야 하므로 <mark style='background-color: #dcffe4'>if, else if, else</mark> 를 통해 각각 조건을 주겠습니다.<br>
<br> 나온결과를 따로 식을 만들지 않고 <mark style='background-color: #dcffe4'>if</mark>문에서 <mark style='background-color: #dcffe4'>Console.WriteLine</mark>으로 바로 출력하도록 했습니다.
