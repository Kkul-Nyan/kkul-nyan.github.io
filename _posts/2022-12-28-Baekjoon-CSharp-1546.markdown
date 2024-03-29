---
layout: post
title:  C# 백준 1546
date:   2022-12-28
image: C.webp
tags: [C#, 백준]
---

---
### 백준 1차원배열 1546
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

            string[] str = Console.ReadLine().Split();
            double[] num = new double[str.Length];
    
            for (int i = 0; i < str.Length; i++)
            {
                num[i] = int.Parse(str[i]);
            }

            for(int i = 0; i < num.Length-1; i++)
            {
                for(int j= i+1; j<num.Length; j++)
                {
                    if (num[i] > num[j])
                    {
                        double tram = num[j];
                        num[j] = num[i];
                        num[i] = tram;
                    }
                }
            }
            double total = 0;
            double max = num[num.Length - 1];


            for (int i= 0; i < num.Length; i++)
            {
               total += (num[i] / max * 100);
            }
            double k = total / (num.Length);
            Console.WriteLine(k);
        }
    }
}
```
## 평균
  - 과목의 갯수를 받은뒤, 모든점수를 최대값을 기준으로 점수/(최고점수*100)으로 변환한뒤 평균값을 구한다.
  - 입력 : 첫째줄에 과목갯수를 알려주는 N과 N갯수만큼의 점수가 주어집니다. 
  - 조건 
      - 먼저 입력값 중 최고점수를 찾아줍니다.
      - 최고점수를 기준으로, 다른점수들을 변환해줍니다.
      - 변환된 점수들을 이용하여, 평균값을 구합니다.<BR>
  - 출력 : 구해진 평균값을 출력해줍니다.<br><br>

가장먼저, 입력값을 받아줍니다. 몇개가 주어지는지 알려주지만, 사실 그렇게 중요하지는 않습니다. 이값을 사용해줘도 되지만, <mark style='background-color: #dcffe4'>어차피 중요한건 조건에 맞게 가공할 2번째 입력값들입니다.</mark>

두번째 입력값을, Split()을 통해 string집합을 선언해 주면서 받아줍니다.
<mark style='background-color: #dcffe4'>Split()로 인해 공백을 기준으로 나누어 들어오게됩니다.</mark> 따라서 string[]집합의 갯수가 N과 동일합니다. num[]의경우, 계산을위해 string을 int형으로 변경해주기 위해 미리 선언해줍니다. for반복문을 통해 string[]집합을 값을 계산할수 있게 int형으로 형변환을 해줍니다. 

주어진 조건되로 값을 가공하기 위해, 변형된 값을 for반복문을 통해 만들어준 <mark style='background-color: #dcffe4'>차순정리식으로 정리</mark>해줍니다. 결국 이렇게되면 num[N or num.Length-1]의 마지막 숫자는  가장 큰 숫자입니다.

이제 가장 큰 숫자를 기준으로 다른 숫자들을 변형함과 동시에 어차피 평균값을 구하기 위해 전부 더해줘야하니, 미리 더해주도록하겠습니다. for반복문을 통해 모든값들을 변형해주고 반복할때마다 <mark style='background-color: #dcffe4'>미리 선언해준 total에다가 더해주겠습니다.</mark>

이렇게 구해진 total을 평균값을 위해 N or num.Length로 나누어 <mark style='background-color: #dcffe4'>평균값을 구해주겠습니다.</mark>

마지막으로, 구해진 평균값 k를 Console.WriteLine으로 출력해주겠습니다.