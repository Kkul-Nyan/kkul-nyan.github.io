---
layout: post
title:  C# 백준 10871
date:   2022-12-21
image: C.webp
tags: [C#, 백준]
---

---
### 백준 1차원배열 10871
---
```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class question10871
    {
        static void Main(string[] args)
        {
            string[] str = Console.ReadLine().Split();
            int N =int.Parse(str[0]); int X =int.Parse(str[1]);
            
            string[] chars = Console.ReadLine().Split();
            int[] A = new int[N];

            for (int i = 0; i < N; i++)
            {
                A[i] = int.Parse(chars[i]);
            }

            for (int i = 0; i < N; i++)
            {
                if (A[i] < X)
                {
                    Console.Write(Nums[i]);
                    Console.Write(" ");
                }
            }
        }
    }
}
```

## X보다 작은 수
  - 주어진 수열에서 주어진 수보다 작은 숫자를 구해야합니다.
  - 작은숫자라는 조건이 있으므로 조건문 + 숫자만큼의 반복해야하므로 반복문 입니다.
  - 입력 : 첫줄에서 둘째줄에 들어올 수열의 갯수 N과 조건의 기준이 되어줄 X, 그리고 N개 만큼의 숫자가 입력됩니다.
  - 조건 
      - 먼저 N의 역할은 X보다 작은수를 판단하는 조건문이 몇번 반복해야하는지를 알려줍니다.
      - X를 기준으로 X보다 작은 수인지를 판단할 조건문이 필요합니다.<BR>
  - 출력 : 조건에 따라 조건문을 반복시켜 얻은 결과 물을 출력해줍니다. 입력받은되로 출력하면 되고, 숫자 사이는 공백이 필요하다고 합니다.<br><br>

먼저 입력 조건에 따라 입력식을 만들어 줍니다.
2개의 문자열이 입력되므로 string을 통해 받아주며, 동시에 <mark style='background-color: #dcffe4'>Console.ReadLine().Split</mark>로 문자열을 구분해준뒤 <mark style='background-color: #dcffe4'>[]</mark>을 사용하여 집합을 만들어줍니다.
각각 사용하기 편하게, 주어진 알파뱃을 그래도 사용해서 N(반복횟수)와 조건문의 기준이되어주는 X로 구분해주면서 string을 int형으로 변환해줍니다.<br><br>
두번째 입력조건인 N개 만큼의 숫자를 입력 받아야합니다. 먼저, N개만큼의 A를 받아야하므로 미리 int형 집합을 선언해줍니다.
바로 <mark style='background-color: #dcffe4'>for반복문</mark>를 통해 N만큼 반복해서 입력값을 받아주면서 바로바로 int형으로 변환한뒤 Nums[]에 받아줍니다.<br><br>
이제 조건에 맞춰 조건문을 만들어서 X와 각 숫자를 비교해 주어야합니다.
먼저, 주어진 숫자만큼 X와 비교를 해주어야하니 <mark style='background-color: #dcffe4'>for반복문</mark>으로 N번만큼 반복해줍니다.
<mark style='background-color: #dcffe4'>if조건문</mark>에서 순서되로 X와 비교해서 X보다 작으면 정해진 규칙되로 <mark style='background-color: #dcffe4'>Console.Write</mark>를 통해 X보다 작은수를 출력해주고, 출력조건에 맞게 공백도 출력해줍니다.
<br><br>
마지막으로 두번째와 3번째 만든 부분을 봐보시면 같은 반복문이 반복되는것을 알수있습니다. 
사실 반복문을 2번 반복할 필요없습니다. 오름차순 내림차순같은 정렬조건이 없는 만큼 입력순서가 곧 출력순서입니다.
<mark style='background-color: #dcffe4'>즉, 2개의 반복문을 합쳐서 2번째줄을 입력받음과 동시에 조건문에 부합되는 A들을 바로바로 출력해주어도됩니다.</mark>


