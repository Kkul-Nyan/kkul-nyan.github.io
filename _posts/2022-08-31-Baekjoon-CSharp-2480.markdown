---
layout: post
title:  C# 백준 2480
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 조건문 2480
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 2480
    {
        static void Main(string[] args)
        {
            string[] Num = Console.ReadLine().Split();

            int A = int.Parse(Num[0]);
            int B = int.Parse(Num[1]);
            int C = int.Parse(Num[2]);

            if (A==B && B==C && A==C)
            {
                int All = 10000 + A * 1000;
                Console.WriteLine(All);
            }
            else if (A==B && A != C)
            {
                    int case1 = 1000 + A * 100;
                    Console.WriteLine(case1);
            }
            else if (B == C && A != B)
            {
                    int case2 = 1000 + B * 100;
                    Console.WriteLine(case2);
            }
            else if (A == C && B != C )
            {
                    int case3 = 1000 + C * 100;
                    Console.WriteLine(case3);
            }
            else
            {
                if (A > B && A > C)
                {
                    int case4 = A * 100;
                    Console.WriteLine(case4);
                }
                else if (B > A && B > C)
                {
                    int case5 = B * 100;
                    Console.WriteLine(case5);
                }
                else
                {
                    int case6 = C * 100;
                    Console.WriteLine(case6);
                }
            }
        }   
    }
}
```

## 주사위 세개

  - 입력 : 한줄에 3개의 정수가 주어집니다.<br>
  - 조건 
      - 정수 3개가 동일할시 10000 + 주사위 눈 X 1000원
      - 정수 2개가 같은 경우, 1000 + 주사위 눈 X 100원
      - 정수가 모두 다른 경우, 100 + 가장 큰 주사위 눈 X 10원
  - 출력 : 조건에 맞게 계산된 상금을 출력합니다.<br>

<br><Br>

입력조건에 맞게 3개의 정수를 <mark style='background-color: #dcffe4'>string[]</mark> 문자열집합으로 받아줍니다.<br>
입력받은 문자열 집합을 <mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 각각 정수형으로 변환해줍니다<br><br>

주사위의 조건을 생각해줍니다.<br>
  - 첫번쨰 조건에 맞는 경우는 1가지 입니다<br><br>

  - 두번쨰 조건에 맞는 경우는
    - A와B는 같지만 A와 C는 다른경우
    - A와C는 같지만 B와 C는 다른경우
    - B와C는 같지만 A와 B는 다른경우
    - 이경우일때만 숫자가 2개는 같고, 하나는 다른경우가 됩니다.<br><br>

  - 세번째 조건은 **나머지 전부**이지만, **가장 큰 눈으로 계산**해야하므로 A,B,C눈을 각각비교해서 제일 큰 숫를 찾아야합니다 
    - A가 가장 큰 경우(A>B이면서 A>C인경우)
    - B가 가장 큰 경우(B>A이면서 B>C인경우)
    - C가 가장 큰 경우(C>A이면서 C>B인경우)
<br>

위의 경우들이 나올수 있는 **모든 경우의 조건**입니다. <br>이 조건에 맞게  <mark style='background-color: #dcffe4'>if 조건문 </mark>을 작성해 주었습니다.

위조건에 맞게 나온 값을 출력조건에 맞게 <mark style='background-color: #dcffe4'>Console.WriteLine(" ")</mark>으로 바로 출력되게 해주었습니다


