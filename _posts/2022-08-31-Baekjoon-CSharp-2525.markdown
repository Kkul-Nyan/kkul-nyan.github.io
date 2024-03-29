---
layout: post
title:  C# 백준 2525
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 조건문 2525
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 2525
    {
        static void Main(string[] args)
        {
            string [] str = Console.ReadLine().Split();
            string C = Console.ReadLine();

            int H = int.Parse(str[0]);
            int M = int.Parse(str[1]);
            int CookTime = int.Parse(C);

            int HM = H * 60;
            int TotalTime = HM + M;
            
            int TC = TotalTime + CookTime;
            int FinishH = TC / 60;
            int FinishM = TC % 60;

            if (TC < 1440)
            { Console.WriteLine(FinishH + " " + FinishM); }
            else
            { 
                int OverTime = TC - 1440;
                int OverH = OverTime / 60;
                int OoverM = OverTime % 60;
                Console.WriteLine(OverH+" "+OverM);
            }

        }
    }
}
```

## 오븐시계
  - 입력 : 값이 2줄입니다. 첫번째줄은 현재시간, 두번쨰시간은 요리시간 C입니다.
  - 출력 : 요리 완료되는 시간을 출력합니다
    - 요리완료되는 시간은 24시간 체계입니다.<br><br>

이전 문제인 2884문제와 흡사합니다.<br>
입력값이 2줄에 나누어서 들어오기떄문에 2번의 입력값을 받아줍니다<br>
첫번쨰 입력값은 문자열 집합으로 입력값을 받아줍니다.<br>
두번쨰 입력값은 문자열로 받아줍니다.<br>
각각의 입력값은 문자열로 받았기때문에, <mark style='background-color: #dcffe4'>int.Parse</mark>를 이용해 정수형으로 바꾸어 바꾸어줍니다. 

<mark style='background-color: #dcffe4'>(int HM)</mark>최소 단위가 분이므로 받아준 시간 입력값을 분으로 바꾸어줍니다<br>
<mark style='background-color: #dcffe4'>(int TotalTime)</mark> 주어진 시간과 분으로 총시간을 계산해줍니다<br>
<br>

24시간체계이기떄문에 23:15분 이상일 경우 00으로 단위가 바뀌게 됩니다.<br>
이를 통해, 요리시간이 더해졌을때 **시간이 바뀌는 경우와 아닌 경우**로 나누어 줍니다<br>
이를 식으로 표현하면,<br><br>

  - TotalTime + CookTime > 1440<br><br>

이 됩니다<br>

### 첫번쨰 시간이 바뀌지 않는 경우,<br>
간단하게 **총시간에 60을 나누어** 몫은 H 나머지는 M이됩니다.<br><br>

### 두번쨰 경우<br>
총시간에 **24시간 * 60분**을 뺴준 시간을 기준으로<br>
몫은 H 나머지는 M이 됩니다.



