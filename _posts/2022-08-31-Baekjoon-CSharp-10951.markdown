---
layout: post
title:  C# 백준 10951
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 반복문 10951
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 10951
    {
        static void Main(string[] args)
        {
            int i = 0;
            while (true)
            {
                string s = Console.ReadLine();
                if (s == null)
                { break; }
                string[] str = s.Split();
                int A = int.Parse(str[0]); int B = int.Parse(str[1]);
                int C = A + B;
                Console.WriteLine(C);
            }
        }
    }
}
```

## A+B - 4
  - 반복문과 가정법을 섞은 문제입니다.
  - 입력 : 2개의 정수가 계속 주어진다. 반복횟수가 주지않는다.
  - 조건 : 주어진 입력값 A와 B를 계속더해준다.
  - 출력 : 더해준 숫자를 출력해준다.<br><br>

입력조건이 까다롭습니다. **몇개의 반복횟수가 진행되는지 알수없기**떄문입니다.<br>
따라서 <mark style='background-color: #dcffe4'>break</mark>를 통해 반복문을 중단하도록 해야합니다.<br><br>

<mark style='background-color: #dcffe4'>while반복문</mark>을 통해, 계속 무한히 반복해주면서 <mark style='background-color: #dcffe4'>if문</mark>을 통해 특정조건이 만족할시<br> <mark style='background-color: #dcffe4'>break</mark>를 통해 멈추도록하겠습니다.<br>
<mark style='background-color: #dcffe4'>string s</mark>를 통핼 입력값을 받아줍니다.<br>
<mark style='background-color: #dcffe4'>if문</mark>의 경우 만약 s에 입력값이 입력되지 않으면 아무것도없다는 null이 되고,<br>
<mark style='background-color: #dcffe4'>if문</mark>에서 s=null로 반단되시 break가 동작해서 while반복문이 멈추게됩니다.<br>

그 이후는 간단합니다. <br>
받아준 입렵값을 <mark style='background-color: #dcffe4'>Split</mark>를 통해 A와 B로 나누어 준 뒤,<br>
A와 B를 더해주고 <mark style='background-color: #dcffe4'>Console.WriteLine</mark>을 통해 출력해줍니다.


