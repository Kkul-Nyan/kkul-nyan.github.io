---
layout: post
title:  C# 백준 9498
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 조건문 9498
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 9498
    {
        static void Main(string[] args)
        {
            string str1 = Console.ReadLine();

            int A = int.Parse(str1);

            if (A > 89)
            {
                Console.WriteLine("A");
            }
            else if (90 > A && A > 79)
            {
                Console.WriteLine("B");
            }
            else if (80 > A && A > 69)
            {
                Console.WriteLine("C");
            }
            else if (70 > A && A > 59)
            {
                Console.WriteLine("D");
            }
            else
            {
                Console.WriteLine("F");
            }
        }
    }
}
```

## 기본적인 가정법 사용 문제입니다<br>
  - If 혹은 Shich문으로 간단하게 각 조건을 적어주어 풀이 가능합니다<br>
  - 각 조건을 적을떄 >,<문이 점수를 포함하는지 안하는지를 유의해줘야합니다