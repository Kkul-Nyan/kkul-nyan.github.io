---
layout: post
title:  C# 백준 14681
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 조건문 14681
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 14681
    {
        static void Main(string[] args)
        {
            string Num1 = Console.ReadLine();
            string Num2 = Console.ReadLine();

            int x = int.Parse(Num1);
            int y = int.Parse(Num2);

            if(x>0 && y>0)
            { Console.WriteLine("1"); }
            else if(x<0 && y>0)
            { Console.WriteLine("2"); }
            else if(x<0 && y<0)
            { Console.WriteLine("3"); } 
            else
            { Console.WriteLine("4"); }

        }
    }
}
```
## 사분면 고르기
  - 입력 : 2줄에 나누어서 2개의 정수가 주어진다
    - 2줄로 나누어 들어오기 떄문에 2번의 입력값을 받아주어야한다.
  - 출력 : 2개의 정수를 (X,Y)좌표로 어떤 사분면인지 출력해준다.
    - 4사분면에 맞게 조건 4가지를 생각합니다.
    - 1사분면 (x , y)
    - 2사분면 (-x, y)
    - 3사분면 (-x, -y)
    - 4사분면 (x, -y)
  <br><br>

2번의 <mark style='background-color: #dcffe4'>Console.ReadLine()</mark>를 통해 입력값을 받아줍니다.<br>
<mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 문자열 입력값을 정수형으로 변경해줍니다.<br>
미리 주어진 조건에 맞게 if조건문을 작성해서<br> Console.WriteLine(" ")으로 미리 정해진 문자열을 출력시킵니다





