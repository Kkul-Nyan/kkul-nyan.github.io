---
layout: post
title:  C# 백준 11022
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 11022
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 11022
    {
        static void Main(string[] args)
        {
            int T = int.Parse(Console.ReadLine());

            for (int j = 0; j < T; j++)
            {
                string[] str = Console.ReadLine().Split();

                Console.WriteLine("Case #" + 
                                   (j + 1) + 
                                    ": " +
                                     "" + 
                                int.Parse(str[0]) +
                                     " + " + 
                                int.Parse(str[1]) + 
                                    " = " + 
                                (int.Parse(str[0]) + int.Parse(str[1])));
            }
        }
    }
}
```

## A+B - 8
  - 이전 문제였던 11021과 비슷한 문제입니다.
  - 입력 : 첫줄에 반복횟수 T,두번쨰줄부터 T횟수만큼 0이하의 A,B 정수값
  - 조건 : A+B를 T번 만큼 반복
  - 출력 : A+B의 합계값을 T번만큼 정해진 형식으로 출력<br><br>

출력 조건만 제외하고는 11021 문제와 비슷합니다.<br>
입력 조건에 따라 첫째줄 입력을 받아주고, 그 입력값을 기반으로 반복문을 통해 입력값을 받아주며,<br> 
굳이 따로 반복문을 만들지 않고 조건에 맞게 입력값을 가공해준뒤,<br>
출력조건에 맞게 출력해주겠습니다<br>
**그러나, 입력,출력,조건 모두 반복 횟수가 동일 하므로 한 반복문에 처리하겠습니다**<br>

<mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 입력값을 문자열로 받자 말자 정수형으로 변환해줍니다.<br>
이 이후 모두 동일한 반복 횟수와 절차에 따르기 떄문에 하나의 반복문으로 처리해주겠습니다.<br>

<mark style='background-color: #dcffe4'>string[] str</mark>로 입력값을 받아주겠습니다. <br>
따로 조건에 따라 계산하지 않고, **출력과 계산을 동시**에 해주겠습니다.<br>
따라서, 따로 **정수형을 선언하지 않겠습니다.**<br><br>

Console.WriteLine()으로 조건에 맞게 출력되게하며, 바로 덧샘 계산이 되도록 했습니다.




  


