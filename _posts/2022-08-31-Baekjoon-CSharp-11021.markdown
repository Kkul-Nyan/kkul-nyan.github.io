---
layout: post
title:  C# 백준 11021
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 11021
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 11021
    {
        static void Main(string[] args)
        {
            int T = int.Parse(Console.ReadLine());
            int[] nums = new int[T];

            for(int i = 0; i < T ; i++)
            {
                string[] str = Console.ReadLine().Split();
                nums[i] = int.Parse(str[0])+int.Parse(str[1]);
            }

            Console.Clear();  

            for(int i = 0; i < nums.Length; i++)
            {
                Console.WriteLine($"Case #{i+1}: " + nums[i]);
            }
        }
    }
}
```

## A+B - 7
  - 입력 : 첫줄에 반복횟수 T,두번쨰줄부터 T횟수만큼 0이하의 A,B 정수값
  - 조건 : A+B를 T번 만큼 반복
  - 출력 : A+B의 합계값을 T번만큼 정해진 형식으로 출력<br><br>

입력, 조건, 출력에 따라 필요한 식과 선언해줄 형을 생각해줍니다.<br>
T번 반복해서 입력받고 더해줄 반복문, T번 반복해서 출력해줄 반복문 **총 2개의 반복문**<br>
제시된 반복횟수를 받아줄 **정수형**, 2번째줄 부터 받아줄 **문자열집합과 정수집합**, 더해질 **a와 b 정수형**, a+b의 합계인 **정수형**이 필요합니다.<br>

따라서, <mark style='background-color: #dcffe4'>int.Parse(Console.ReadLine())</mark>를 통해 반복횟수 T값을 받아주고,<br>
T횟수만큼 a+b가 더해질 정수집합 <mark style='background-color: #dcffe4'>nums[]</mark>를 선언해줍니다.

<mark style='background-color: #dcffe4'>for반복문</mark>을 통해 T번 만큼 입력값을 받고,<br>
받은 입력값을 각각 바로 <mark style='background-color: #dcffe4'>int.Parse</mark>를 통해 정수형으로 변환해면서 합계를 구해줍니다.

  - **<mark style='background-color: #dcffe4'>Consle.Clrea()</mark>의 경우 콘솔창을 깨끗하게 지워주는식입니다 없어도 상관없습니다.**

입력을 받았고, 바로 계산을한뒤 <mark style='background-color: #dcffe4'>nums[]정수집합</mark>에 값을 모아주었으니,<br>
<mark style='background-color: #dcffe4'>List</mark>와 다르게  <mark style='background-color: #dcffe4'>[]</mark>으로 만든 집함은 <mark style='background-color: #dcffe4'>Count()</mark>가 아닌 <mark style='background-color: #dcffe4'>Length</mark>를 써야 집합 내부의 갯수를 가져올수있습니다.<br><br>
이값을 제시된 출력 형식에 따라 반복문을 이용해서 출력해줍니다.

