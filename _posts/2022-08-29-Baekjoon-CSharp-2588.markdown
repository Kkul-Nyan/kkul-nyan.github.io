---
layout: post
title:  C# 백준 2588
date:   2022-08-29
image: C.webp
tags: [C#, 백준]
---

---
### 백준 입출력과사칙연산 2588
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 2588
    {
        static void Main(string[] args)
        {
            string A = Console.ReadLine();
            string B = Console.ReadLine();

            int C = int.Parse(A);
            int D = int.Parse(B.Substring(0,1));
            int E = int.Parse(B.Substring(1,1));
            int F = int.Parse(B.Substring(2,1));
            int G = int.Parse(B);


            Console.WriteLine(C*F);   
            Console.WriteLine(C*E);
            Console.WriteLine(C*D);
            Console.WriteLine(C*G);
        }
    }

}
```
### 가장 먼저 입력 조건과 출력 조건을 확인하겠습니다.
  - 첫째 줄에 (1)의 위치에 들어갈 세 자리 자연수가, 둘째 줄에 (2)의 위치에 들어갈 세자리 자연수가 주어진다.
    - 2줄의 정수값이 입력될것이 확인됩니다. 입력값을 2번 받을것을 염두해둡니다.
  - 첫째 줄부터 넷째 줄까지 차례대로 (3), (4), (5), (6)에 들어갈 값을 출력한다.
    - 4줄로 출력값을 내보내야할것이 확인됩니다. 따라서 <mark style='background-color: #dcffe4'> WriteLine() </mark>를 염두해둡니다.<br><br>

입력값을 <mark style='background-color: #dcffe4'> ReadLine() </mark>를 2번 받습니다.<br>
문자형으로 값을 받았기 때문에 <mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 정수형으로 변경해줍니다. 
두번쨰 입력값의 각 자리수가 필요하기 떄문에 <mark style='background-color: #dcffe4'>Substring</mark>를 통해 따로 변수화 해줍니다.<br><br>
출력 조건에 맞게 <mark style='background-color: #dcffe4'>Console.WriteLine</mark> 혹은 <mark style='background-color: #dcffe4'>Write</mark>에 줄나누기 명령어를 넣어서 출력해줍니다.
