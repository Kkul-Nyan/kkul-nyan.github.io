---
layout: post
title:  C# 백준 2739
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 2739
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 2739
    {
        static void Main(string[] args)
        {
            int Num = int.Parse(Console.ReadLine());
            int Total = 0;
            
            for(int i = 1; i < 10; i++)
            { 
                Total = Num * i;
                Console.WriteLine($"{Num} * {i} = "+Total);
            }
        }

    }
}
```

### 구구단
  - 입력 : 정수 1개가 주어진다(1~9)
  - 조건 : 입력값을 N = 1 ~ 9까지 각각 곱해줍니다.(9번) 
  - 출력 : N = 1~9까지 한줄 마다  **입력값 * N = 곱샘값**을 출력합니다.
<mark style='background-color: #dcffe4'>int.Parse</mark>를 통해서 문자열 입력값을 바로 정수형으로 입력받습니다.<br><br>

조건에 맞게 식을 구해야합니다. 입력값을 1~9까지 총 9번 차례되로 곱해야합니다<br>
반복되는 조건과 횟수가 추정되므로 반복문을 통해 반복해줍니다<br><br>
<mark style='background-color: #dcffe4'>for반복문</mark>을 사용합니다.<br> 
<mark style='background-color: #dcffe4'>for반복문</mark>의 형식은<br> 
  -  for(int i = 1(시작조건); i<10(종료조건); i++(반복시 변경값)){계산식}입니다. <br>

조건식에 맞게 1부터 곱해야하니 i = 1, 총 9까지 곱하므로 i<10, 한번 반복할떄마다 1씩 추가 되므로 i++로 해줍니다.<br><br>

출력조건은 한줄마다 나와야 하므로 <mark style='background-color: #dcffe4'>fConsole.WriteLine()</mark>으로 출력해줍니다.



