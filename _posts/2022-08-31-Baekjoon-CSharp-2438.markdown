---
layout: post
title:  C# 백준 2438	
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 2438	
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 2438
    {
        static void Main(string[] args)
        {
            int T = int.Parse(Console.ReadLine());
            Console.Clear();
            for(int i = 1; i < T+1 ; i++)
            {
                int j = 0;
                while (j != i)
                {
                    Console.Write("*");
                    j++;
                }
                Console.WriteLine();
            }
        }
    }
}
```

## 별찍기 - 1
  - 단순한 식을 반복시키는 기본적인 이중 반복문 무제입니다.
  - 입력 : 반복할 횟수인 정수형 T가 입력됩니다.
  - 조건 : 5줄 반복, 별하나씩 증가 반복
  - 출력 : 한줄당 *하나씩 증가하며 T만큼 반복해줍니다<br><br>

입력조건에 맞게 <mark style='background-color: #dcffe4'>int.Parse(Console.ReadLine())</mark>로 문자입력값을 정수형으로 변환해줍니다.<br>
T횟수만큼 반복하면서 줄이 늘어나야하므로,<br>
for 반복문을 통해 T만큼 반복하게하고 <mark style='background-color: #dcffe4'>Console.WriteLine()</mark>으로 한번반복할때마다 줄을 나누어줍니다.<br><br>

별을 갯수도 한줄마다 증가해야합니다 별을 갯수는 현재반복횟수와 동일 하다는것을 알수있습니다.<br>
따라서, 반복문을 하나 더써주겠습니다.<br><mark style='background-color: #dcffe4'>for 대신 while 반복문</mark>을 써주겠습니다.<br><br>
새로운 정수 j를 선언해주고 j가 현재반복횟수보다 적으면 별을 하나씩 반복하면서 출력하게했습니다.<br>
예를 들어 3번째 반복 횟수일때, 3번째 줄이되고,<br> 3번째줄에서 j는 **0,1,2** 가되면서 반복하면서 한번 반복할때마다 별을 한번씩 출력하게됩니다.
