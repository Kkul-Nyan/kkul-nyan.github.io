---
layout: post
title:  C# 백준 2439
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 2439
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 2439
    {
        static void Main(string[] args)
        {
            int T = int.Parse(Console.ReadLine());
            Console.Clear();
            for (int i = 1; i < T + 1; i++)
            {
                for(int j= T; j > i; j-- )
                {
                    Console.Write(" ");
                }
                for(int k= 0; k < i ; k++)
                {
                    Console.Write("*");
                }
                Console.WriteLine();
            }
        }
    }
}
```

## 별찍기 - 2
  - 단순한 식을 반복시키는 이중 반복문 무제입니다.
  - 입력 : 반복할 횟수인 정수형 T가 입력됩니다.
  - 조건 : 5줄 반복, 공란 1칸 감소, 별하나씩 증가 반복
  - 출력 : 한줄당 공란 하나씩 감소, *하나씩 증가하며 T만큼 반복해줍니다<br><br>



반복횟수를 <mark style='background-color: #dcffe4'>int.Parse(Console.ReadLine())</mark>를 이용해서 입력값을 받자말자 정수형으로 변환해줍니다.<br><br>

<mark style='background-color: #dcffe4'>T번 반복하기 위한 반복문, 한번반복때마다 공란 한칸 감소하는 반복문, 별하나가 증가하는 반복문</mark><br>
이렇게 3종류가 필요할것입니다. 공란이 먼저들어가고 별이 들어오기때문에,<br>  공란 반복문이 별 반복문보다 이전에 작동하게 해줘야합니다<br> 
공란 반복문은 공식으로 생각하면 총반복횟수에서 n+1 이 반복해서 빼져가는 방식입니다.
따라서 for반복문에서 **j값은 총반복횟수 이며, 반복이 진행될때마나 하나씩 줄여 가게 해줍니다**.

별을 찍는 반복문은 위의 반복문과 달리 **현반복횟수 = 별갯수** 입니다.
k는 현 반복횟수 만큼만 반복되게해주고, 현반복횟수와 동일 반복이 되면 반복을 멈추게해줍니다.


