---
layout: post
title:  C# 백준 4673
date:   2022-12-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 함수 4673
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
            int i = 1;
            List<int> self = new List<int>();
            while (i <= 10000)
            {
                bool k = true;
                for (int j = 1; j <= 10000; j++)
                {
                    int one = j % 10;
                    int ten = (j / 10) % 10;
                    int hun = (j / 100) % 10;
                    int thu = (j / 1000) % 10;
                    int drnum = j + one + ten + hun + thu;
                    
                    if (i == drnum)
                    {
                        k = false;
                    }
                }
                if(k == true)
                {
                    self.Add(i);
                }
                i++;
            }
            foreach(var y in self)
            { Console.WriteLine(y); }

        }
    }
}
```

## 셀프넘버
  - 어떤수 X일떄 X의 1의자리, 10자의,100의자리, 1000의 자리의 앞자리를 더해서 다시 새로운 숫자를 만들수 있는 수입니다. 이런 X가 없는 10000이하의 숫자를 찾는것입니다.
  - 입력 : 입력값은 없습니다. 10000이하의 모든수를 조사해야합니다.
  - 조건 
      - 일단 생성자X 가 존재하는 모든 숫자를 찾아줍니다.
      - 10000이하의 수에서 X를 제거해줍니다. 그러면 남은 수들은 생성자X가없는 셀프넘버입니다.<BR>
  - 출력 : 구해진 셀프넘버를 한줄에 하나씩 출력해줍니다.<br><br>

  입력값이 없지만, <mark style='background-color: #dcffe4'>10000이라는 제한은 있습니다. 셀프넘버역시 X가 존재하지 않는수이고, X의 조건은 주어졌습니다.10000 이하의 수에서 모든 X를 가진수를 제거해주면 되겠습니다.</mark>
  가장먼저 체크를 시작할 숫자인 int i = 1을 선언해주고, 셀프넘버를 담아줄 List를 선언해 줍니다.

  while반복문을 통해 10000까지의 반복을 시작합니다.
  마지막에 숫자를 증가시키고 1부터 시작이기때문에 같거나 작거나가(=<) 아닌 작으면(<)으로 선언합니다
  bool값을 선언해서 셀프넘버면 List에 담을것이고, 아니면 담지 않도록 체크하도록 선언해줍니다.

  이제 for 반복문을 통해 i가 특정숫자일떄 j역시 10000이하에서 i의 생성자가 될수 있는지를 확인해줍니다.
  <mark style='background-color: #dcffe4'>i역시 1~10000사이에 어떤생성자가 존재하는지 알수 없기때문에, for반복문을 통해 일일히 테스트를 해줘야합니다.</mark>
  생성자는 원래숫자인 j와 j의 1의자리, 10의자리, 100의자리,1000의 자리의 수의 합입니다. 
  각 자리를 원하는 자리수로 나누어주면 그자리의 숫자이하는 버려지게되고, 그숫자를 나머지 연산을 통해서 그자리 이상도 버려지게됩니다.
  예를들어, 1010에서 10의 자리를 원한다면 10의자리수로 나누어서 101을 구하고, 그위에 자리를 %10 나머지 연산을 통해 100을 버리고 나머지인 1을 구해주는방법입니다.
  이렇게 구해진 숫자를 i와 비교해서 일치하게된다면, i의 생성자인 j가 존재 하는것이기 때문에 k를 false로 두고 저장하지 않습니다.
  만약 이렇게 10000까지 체크했는데도 생성자가 없으면 k는 true값을 유지하고 List에 i값이 저장되게됩니다.
  반복문의 끝에서 i의 숫자를 증가 시키면 됩니다. 
  i가 1증가된 상태로 다시 while반복문이 10000이하까지 반복하게됩니다.

  이렇게 구해진 self넘버를 한줄당 하나씩 출력해주면됩니다. <mark style='background-color: #dcffe4'>반복문을 통해 출력해도되고, 사실 while문에서 구해지자 말자, 따로 List에 담지말고 바로바로 출력해주어도됩니다.</mark>