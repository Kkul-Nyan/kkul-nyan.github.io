---
layout: post
title:  C# 백준 10952
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 10952
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 10925
    {
        static void Main(string[] args)
        {
            while (true)
            {
                string[] str = Console.ReadLine().Split();
                
                int Num = int.Parse(str[0]) + int.Parse(str[1]);
                if( Num==0)
                { break; }
                Console.WriteLine(Num);
            }
        }
    }
}
```

## A+B - 5
  - 반복문과 가정법을 섞은 문제입니다.
  - 입력 : 2개의 정수가 계속 주어진다.
  - 조건 : 주어진 2개의 정수를 계속 더해준다. 2개의 0의 정수가 주어지면 반복을 중단한다.
  - 출력 : 더해준 숫자를 출력해준다.<br><br>

전 이문제가 까다로웠습니다. 원래 반복횟수가 주어져서 <mark style='background-color: #dcffe4'>for</mark>로 반복문을 많이 쓴 폐해였습니다.<br>
이 문제는 종료조건인 2개의 0이 주어지기 전까지 무한히 반복해야 합니다.<br>
따라서 <mark style='background-color: #dcffe4'>for 반복문</mark>을 사용할수 없습니다.<br><br>

<mark style='background-color: #dcffe4'>while반복문</mark>과 <mark style='background-color: #dcffe4'>break</mark>를 통해 계속되는 반복문을 조건에 따라 멈추도록 만들겠습니다.<br><br>

먼저 <mark style='background-color: #dcffe4'>while 반복문</mark>을 선언해줍니다. 조건은 true값이면 계속 반복해주는 방식입니다.<br>
반복문 내부에서  <mark style='background-color: #dcffe4'>string[] str</mark>를 통해 문자열 집합으로 2개의 정수를 받아줍니다.<br>
2개의 정수가 0이 나온다로 조건을 해도 되지만,<br>
**2개의 0을 합쳐도 0이기때문에 간단히 2개의 정수의 합계가 0이 아니면 계속 반복되게 하겠습니다.**<br><br>

입력받은 2개의 값은 바로 <mark style='background-color: #dcffe4'>int.Parse</mark>로 정수형으로 변환과 동시에 조건에 맞게 두정수를 합쳐주겠습니다.<br>
if문의 조건의 만약 이 2개의 정수의 합이 0 이면 작동하게 만들었습니다.<br>
만약 2개의 정수가 0으로 주어지고 <mark style='background-color: #dcffe4'>if문</mark>의 조건되로 0이 들어오게 된다면, <br>
<mark style='background-color: #dcffe4'>break</mark>가 작동하게 되고 <mark style='background-color: #dcffe4'>while반복문</mark>은 **중단** 되게 됩니다.<br><br>
