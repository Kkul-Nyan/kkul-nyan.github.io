---
layout: post
title:  C# 백준 2753
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 조건문 2753
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 2753
    {
        static void Main(string[] args)
        {
            string Num = Console.ReadLine();

            int A = int.Parse(Num);
            int B = A % 4;
            int C = A % 100;
            int D = A % 400;

            if (B == 0 && C == 0 && D == 0)
            {
                Console.WriteLine("1");
            }
            else if(B == 0 && C != 0 )
            {
                Console.WriteLine("1");
            }                 
            else
            {
                Console.WriteLine("0");
            }
        }
    }
}
```

## 윤년인지 아닌지를 구분해야합니다.
  - 윤년의 단판하기 위한 변수는 총 3가지입니다.<br>
    - 1. 4의 배수이다.
    - 2. 100으로 나누어 떨어진다.
    - 3. 400으로 나누어 떨어진다.<br><br>
  - 그에 따라 윤년인 조건은 2가지이며, 그외는 윤년이 아닙니다.<br>
    - 1. 3가지 변수가 모두 만족한다.
    - 2. 1번 변수가 만족되지만 2번 변수가 만족되면 안된다.
<br><br>


<mark style='background-color: #dcffe4'> Console.ReadLine()</mark>으로 입력값을 문자열로 받아와줍니다.<br>
받아온 입력값을 <mark style='background-color: #dcffe4'> int.Parse()</mark>를 통해 정수형으로 만들어줍니다<br>
이제 받아온 입력값을 이용해서 미리 정해둔 변수의 조건에 맞게 가공 해줍니다.<br>
<br> 
조건에 따라 결과값은 2가지 조건은 3가지이므로 3가지를 지준으로 <mark style='background-color: #dcffe4'>if</mark>문을 작성해줍니다.

