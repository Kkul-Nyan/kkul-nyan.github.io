---
layout: post
title:  C# 백준 10430
date:   2022-08-29
image: C.webp
tags: [C#, 백준]
---

---
### 백준 입출력과사칙연산 10430
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 10430
    {
        static void Main(string[] args)
        {
            string[] num = Console.ReadLine().Split();
            int A = int.Parse(num[0]);
            int B = int.Parse(num[1]);
            int C = int.Parse(num[2]);

            Console.WriteLine((A+B)%C);
            Console.WriteLine(((A%C)+(B%C))%C);
            Console.WriteLine((A*B)%C);
            Console.WriteLine(((A%C)*(B%C))%C);
        }
    }
}
```
첫째 줄에 (A+B)%C, 둘째 줄에 ((A%C) + (B%C))%C, 셋째 줄에 (A×B)%C, 넷째 줄에 ((A%C) × (B%C))%C를 출력한다.<br><br>
출력 조건을 보니 한줄씩 출력해야하므로 <mark style='background-color: #dcffe4'>WriteLine()</mark>를 염두해둡니다.<br><br>
입력값이 연달아 3개가 입력 되므로  
<mark style='background-color: #dcffe4'> string[]num = Console.ReadLine().Split()</mark>로 값을 받음과 동시에 집합으로 분리해줍니다.<br>
각각 조건에 맞게 int값을 선언해주고 문자로 받은 num을 <mark style='background-color: #dcffe4'> int.Parse</mark>를 통해 정수형으로 변경해줍니다.<br><br>
변수들을 제시된 조건에 맞게 출력해줍니다.



