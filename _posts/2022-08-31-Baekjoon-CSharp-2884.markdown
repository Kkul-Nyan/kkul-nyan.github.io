---
layout: post
title:  C# 백준 2884
date:   2022-08-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 조건문 2884
---

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace question
{
    internal class 2884
    {
        static void Main(string[] args)
        {
            string[] Num = Console.ReadLine().Split();
            
            int H = int.Parse(Num[0]);
            int M = int.Parse(Num[1]);

            int E = (H * 60) + M;

            if (E > 44)
            {
                int H1 = (E - 45) / 60;
                int M1 = (E - 45) % 60;
                Console.WriteLine(H1 + " " + M1);
            }

            else
            {
                int T = 1440 + E;
                int H2 = (T - 45) / 60;
                int M2 = (T - 45) % 60;
                Console.WriteLine(H2+" "+M2);
            }
        }
    }
}
```
## 알람시계
  - 입력 : 한줄에 시간 H와 분 M이 주어집니다.
    - H는 0~23까지 M은0~59까지 정수형이 제시됩니다.
  - 출력 : 45분 일찍 알람을 맞춰야 하므로, 주어진 입력값에서 45분 앞 시간을 출력해줍니다.<br>
    - 시간 특징상 **00:00**을 기준으로 45분이 땡겨지면 시간단위가 23으로 바뀌게 됩니다.(정수 0~23)
    - 시간과 분을 분단위로 바꾼뒤 다시 시간을 나누어서 H와 M을 구해주면됩니다.  
 <br>
 <br>

먼저 <mark style='background-color: #dcffe4'>string[]</mark> 문자열 집합으로 한줄에 입력되는 2개의 숫자를 입력받아줍니다.<br>
각각의 입력된 문자를 <mark style='background-color: #dcffe4'>int.Parse</mark>로 정수형으로 변경해줍니다.(숫자계산을 위해)<br>
첫번째 조건을 생각하면 00시 기준으로 23으로 바뀌거나 아니면 단순히 더해 지는 2가지 조건이란걸 생각합니다</br>
23시로 바뀌는 조건은 00:44분니다. 이에따라 2개의 방정식이 필요합니다.</br></br>
첫번쨰로 시간을 분단위로 바꾸어서 **총시간을 분단위로** 바꾸어줍니다</br>
이 분단위가 44이하라면 앞에 H가 23으로 바뀌게 됩니다.<br> 
이부분이 if조건문에서 염두해둘 조건입니다.<br>
<br>
첫번쨰 방정식인 E>44보다 커서 H가 23으로 바뀔 필요가 없는 방정식은<br>
일단, 시간은 총시간을 60을 나누었을때 **몫**입니다<br>
분의 경우 총시간을 60으로 나누고 남은 **나머지**입니다<br>
따라서 45분 이전시간을 구해야 하니 ***총시간에서 45분을 빼준*** 뒤<br>
각 몫과 나머지가 시간과 분이되고 주어진 출력형식으로 출력해줍니다<br> 
<br>
두번째 방정식은 크게 2가지 방식으로 생각할수있습니다<br>
<br>
  - 1. 무조건 H는 23이다.
  - 2. 음수가 되니까 24시간만큼 더해준다.
<br><br>

1번 방식은 따로 첫번쨰방정식방식에서 시간을 23으로만 고정해주면됩니다.<br>
2번쨰 방식을 위해 **24시간을 60으로 곱해준 뒤**, 기존 총시간에 더해줍니다.<br>
그 기준으로 첫번쨰 방정식과 동일하게 총시간에 45분을 제외해준 뒤<br>
몫은 시간, 나머지는 분이 됩니다.<br>
이렇게 구해진 **H2**와 **M2**를 출력해줍니다







 
