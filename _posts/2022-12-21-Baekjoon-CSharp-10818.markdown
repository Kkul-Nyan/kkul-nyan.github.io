---
layout: post
title:  C# 백준 10818
date:   2022-12-22
image: C.webp
tags: [C#, 백준]
---

---
### 백준 1차원배열 10818
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
            string A = Console.ReadLine();
            int N = int.Parse(A);
            string[] B = Console.ReadLine().Split();
            int[] b = Array.ConvertAll(B, int.Parse);

            int max = -1000000;
            int min = 1000000;
            for (int i = 0; i < N; i++)
            {
                if (b[i] > max)
                {
                    max = b[i];
                }
                if(b[i] < min)
                {
                    min = b[i];
                }    
            }
            Console.WriteLine(min + " " + max);
        }
    }
}
```

## 최소, 최대
  - 최소값과 최대값을 구하는 문제입니다.
  - 제가 좋아하는 방법은 오름차순이나, 내림차순으로 정리해버린 다음 맨앞의 숫자와 맨뒤의 숫자를 출력하는 방법이지만, 이 문제서는 시간 초과가 되어버려서 사용하지 못하고 다른 방법을 찾아야했습니다.
  - 입력 : 첫줄에서 N개의 정수가 주어질지 알려주며, 2번째 줄 입력에서 N개 만큼의 숫자가 주어집니다.(주어진수의 조건은 -1000000~1000000개 사이의 숫자입니다.)
  - 조건 
      - 먼저 N의 역할은 반복문의 반복횟수를 알려줍니다.
      - 처음받은 수부터 비교하되, 만약 비교 기준의 수가 새로운 수보다 크거나 작으면 조건에 맞게  min과 max를 교체해줍니다.<BR>
  - 출력 : 조건문에 따라 max와 min을 지정하고 구했기 때문에, 공백을 사이에 추가한 되로 출력해줍니다.<br><br>

  가장 먼저 입력값을 받아주어서 내부에서 사용하기 위해 필요한 형식으로 변환해줍니다. 먼저 첫번째 입력값을 string으로 받아준뒤 바로 <mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 <mark style='background-color: #dcffe4'>int형</mark>으로 변환해줍니다. 바로 이어서 들어오는 입력값은 <mark style='background-color: #dcffe4'>string[]집합형</mark>으로 받은 뒤, 바로 <mark style='background-color: #dcffe4'>Array.ConvertAll</mark>을 통해 <mark style='background-color: #dcffe4'>int[]</mark>집합형으로 변경해 줍니다. <br><br>

  이제 조건에 맞게 계산을 해야합니다. 최소값과 최대값 2가지 출력값을 찾아야하고, 위에 조건을 정리할떄, N번만큼 반복해야하고 2개의 출력값을 찾아야하니 조건문이 필요합니다.
  먼저, <mark style='background-color: #dcffe4'>for반복문</mark>을 통해서 N번 만큼 반복을 시켜줍니다. 최소값과 최대값을 찾기위해 일단 b[0]의 경우, 무조건 기준값이 되고 이후 들어오느 b[1],b[2], ... 값들과 비교하고, b[0]보다 크거나 작으면, 새로운 숫자로 변경되어 반복되도록 만들어줄 조건문이 필요합니다.<br><br>

  일단, b[0]를 무조건 받아주기위해 처음 max값은 주어지는 숫자의 최소값인 -1000000보다 크다면 값이 변경되도록 합니다. b[]>max는 단순히 처음은 원하는되로 되겠지만, 이게 어떻게 최대값을 구한다는지 헷갈리는분을 위해 자세히설명하자면, <br> i=0인경우, b[0]>max 는 무조건 맞기 때문에 max =b[0]가 됩니다.<br>만약 i=1인경우, b[1]>b[0]인지를 검사하는 조건문이 되고, 거짓이라면 max =b[0]가 유지됩니다. <br>i=2의 경우 b[2]>b[0]인지 검사하게되고, 참이라면 max = b[2]로 변경되어 반복하게됩니다.<br><br>

  따라서, 이렇게 구해준 max 값과 min값을 출력조건에 맞게 사이에 공백을 추가 한뒤 출력해주면됩니다.
