---
layout: post
title:  C# 백준 11720
date:   2022-12-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 문자열 11720
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class question
    {
        static void Main(string[] args)
        {
            int N = int.Parse(Console.ReadLine());
            string str = Console.ReadLine();
            int sum = 0;
           
            for (int i =0; i < N; i++)
            {
                sum += int.Parse(str[i].ToString());

            }
            Console.WriteLine(sum);

        }
    }
}
```

## 숫자의 합
  - 공백없이 나열된 연속된 숫자들의 합을 구하는 문제입니다.
  - 입력 : 첫째줄에 총진행할 갯수 N이 주어집니다. 2번째줄부터는 N개 만큼의 숫자의 반복입니다. 
  - 조건 
      - 먼저 입력값 반복할 횟수를 받아줍니다. 
      - 숫자들을 모두 더해줍니다.<BR>
  - 출력 : 구해진 총합을 출력해줍니다.<br><br>

  <mark style='background-color: #dcffe4'>간단히 string에서 각각의 문자에 접근하는 방법을 알아보는 문제입니다.</mark>
  먼저, 총합을 구해주는 문제이고, 몇번 반복해서 더해야하는지를 알려주므로 반복횟수 N을 받아줍니다.
  공백없이 나열된 숫자를 string으로 받아줍니다.

  이제 이 데이터들을 주어진 조건에 따라 가공하고 총합을 구해주면 됩니다.
  <mark style='background-color: #dcffe4'>string을 경우, 문자열로서 각각의 문자는 str[indexNumber]를 통해 접근할수 있습니다.</mark>
  반복문을 통해 N번 만큼 더해주면서, 각각의 문자는 indexnumber를 i로 대체해서 0부터~N-1까지 반복해주면서
  int.Parse를 통해 int형으로 만들어 주자말자, sum을 통해 총합을 구해줍니다.

  구해진 총합을 출력해주면 완료됩니다.