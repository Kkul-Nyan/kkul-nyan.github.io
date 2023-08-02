---
layout: post
title:  C# 백준 1110
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 1110
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 1110
    {
        static void Main(string[] args)
        {
            int N = int.Parse(Console.ReadLine());

            int num1 = N / 10;
            int num2 = N % 10;
          
            if(N>9)
            {
                int i = 1;
                while (true)
                {
                    int num3 = (num1 + num2) % 10;
                    if (num2 == N / 10 && num3 == N % 10)
                    { break; }
                    num1 = num2;
                    num2 = num3;
                    
                    i ++;
                }
                Console.WriteLine(i);
            }
            else
            {
                num1 = 0;
                int j = 1;
                while (true)
                {
                    int num3 = (num1 + N) % 10;

                    if (num2 == N / 10 && num3 == N % 10)
                    { break; }

                    num1 = num2;
                    num2 = num3;

                    j++;
                }
                Console.WriteLine(j);
            }
        }
    }
}
```

## 더하기 사이클
  - 반복문과 가정법을 섞은 문제입니다.
  - 입력 : 99보다 작거나 같은 정수 N
  - 조건 
      - 주어진 수가 10보다 작다면 앞에 0을 붙여 두 자리 수로 만들고, 각 자리의 숫자를 더한다.
      - 가장 오른쪽 자리 수와 앞에서 구한 합의 가장 오른쪽 자리 수를 이어 붙이면 새로운 수<BR>
      - 새로운 수와 N의 값이 같다면, 반복을 중단한다.<br>
  - 출력 : N의 반복횟수를 출력해준다.<br><br>

주어진 수를 새로운 수로 만들어주면됩니다.<br>
정수 N 을 <mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 입력값을 받아주자말자 정수형으로 변환해줍니다<br>
**첫번째 조건에 따라 N이 10보다 큰지 작은지를 판단**해줍니다.<br>
num1은 10의 자리수, num2는 1의 자리수로 나누어줍니다.<br>
10이하와 10이상일떄 계산식은 크게 다르지않습니다.<br>

먼저,** N이 10이상일 때**입니다.<br>
**반복횟수를 알기위해 정수형을 하나 선언**해줍니다.<br>
무조건 계산을 1번해야하니, 정수를 1로 선언해주고,<br> 정수값의 증가는 계산이 한번 완료되면 증가하게했습니다.<br>
구한 합은 num1 + num2 이고 이 값은 num3 로 선언해주겠습니다.<br>

한번 num1,num2,num3를 구하고 하면, <mark style='background-color: #dcffe4'>if조건문</mark>을 통해 N과 새로운 수가 같은지 확인해줍니다.<br>
새로운 수는 조건2에 따라 가장 오른쪽 자리 수이므로 <u>num2이고 새로운수의 10의 자리수</u>입니다. <br>
num3는 조건2에 따라 구한 합의 가장 오른쪽 숫자 10으로 나누어주고 <br><u>남은 나머지값이자, 새로운수의 1의 자리수</u>입니다.<br>

따라서, **num2가 N의 10의자리와 숫자가 같고, num3가 N의 1의 자리와 숫자가 같으면**<br>
N과 새로운수자 같은 숫자이므로 **계산을 멈추어줍니다**.<br>

만약, 조건이 맞지 않는다면<br>
num값을 앞으로 하나씩 밀어주고(<mark style='background-color: #dcffe4'>num1값에 num2를주고 num2값에 num3</mark>를 줍니다.)<br>
반복횟수를 1회 증가 시키고, 다시 새로운 num3를 구해준뒤,<br>
계산식을 조건문과 맞을떄까지, 계속 반복해줍니다.<br>

N이 0보다 작은경우,<br>
조건 1번에따라 십의 자리인 num1을 0으로 선언해준뒤, 위에 계산식과 <u>동일하게 진행</u>해주면됩니다.<br>

마지막으로, N과 새로운 수가 같다면, **미리 선언해두고 계산해둔 정수형을 출력**해줍니다.<br>
각 정수형의 출력을 <mark style='background-color: #dcffe4'>while문</mark>뒤에 둔 이유는,<br> 각 조건문속에 <mark style='background-color: #dcffe4'>while반복문</mark>이 <mark style='background-color: #dcffe4'>break</mark>로 동작을 멈추어야<br>
출력이 작동하기때문입니다.



