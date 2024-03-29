---
layout: post
title:  C# 백준 10950
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 10950
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 10950
    {
        static void Main(string[] args)
        {
            int T = int.Parse(Console.ReadLine());
            int i = 0;

            while (i < T)
            {
               string[] S = Console.ReadLine().Split();
               int K = int.Parse(S[0]);
               int C = int.Parse(S[1]);
               int D = K + C;
               Console.WriteLine(D);
               i++;
            }     
        }
    }
}
```

## A+B-3
  - 입력 : 첫째줄에 반복할 횟수, 다음줄부터는 횟수만큼 더해야할 2가지 정수
  - 조건 : 주어진 반복횟수에 맞게, 반복문을 통해 합계식을 반복합니다.
  - 출력 : 한줄에 하나씩 계산된 수를 출력합니다.<br><br>

입력조건에 따라 처음 정수는 반복횟수이고, 이를 통해 입력값도 몇번을 받을지를 반복해줍니다.<br>
<mark style='background-color: #dcffe4'>for 반복문</mark>과 <mark style='background-color: #dcffe4'>while 반복문</mark> 중 전 <mark style='background-color: #dcffe4'>while 반복문</mark>을 이용해서 계산하도록하겠습니다<br><Br>
반복횟수를 입력받아야하므로,<br> <mark style='background-color: #dcffe4'>int.Parse(Console.ReadLine())</mark>을 이용해서 입력값을 받음과 동시에 정수형으로 변환해주겠습니다.<br>
<br>
조건에 따라, **T번 반복하면 멈춰**(i < T)야하니   
반복횟수를 확인할 <mark style='background-color: #dcffe4'>int i</mark>값 정의해줍니다.i는 한번 반복할때마다 1씩 증가(i++)해서 T번와같아 멈추도록하겠습니다.  

입력조건에 맞게 2개의 정수가 들어오므로 <mark style='background-color: #dcffe4'>string[]</mark> 문자열집합으로 받아준뒤,<br>
각각 <mark style='background-color: #dcffe4'>int.Parse()</mark>를 통해 정수형으로 변경해줍니다.<br>
그뒤 바로, 2개의 정수를 더해준 뒤,<br>
한줄마다 출력해야하므로 <mark style='background-color: #dcffe4'>Console.WriteLine()</mark>으로 출력해줍니다.<br>
계산이 끝나면 1회 반복이 완료되었으므로 <mark style='background-color: #dcffe4'>i++</mark>를 통해 반복횟수를 증가시켜줍니다<br>
즉, i가 하나씩더해지면서 T의 갯수와 같아지는 순간 반복문이 끝나게됩니다.<br><br>
*만약 i를 편하게 1로 하고싶다면 **i<=T로 조건을 주면됩니다**.




