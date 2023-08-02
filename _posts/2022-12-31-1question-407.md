---
layout: post
title:  C# 백준 8958
date:   2022-12-31
image: C.webp
tags: [C#, 백준]
---

---
### 백준 1차원배열 8958
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
            int[] Final = new int[N];
            
            for (int i = 0; i < N; i++) // 전체 반복문
            {
                string str = Console.ReadLine();                       
                char[] ch = str.ToCharArray();               
                             
                int num = 0;
                int [] Onum = new int[ch.Length]; 
                for (int j = 0; j < ch.Length; j++)
                {
                    if (ch[j] == 'X')
                    {
                         num = 0;
                         Onum[j] = 0;
                    }

                    else
                    {
                        Onum[j] = num + 1;
                        num++;
                    }

                }
                int total = 0;
                for (int H=0; H<Onum.Length; H++)
                {
                    total +=Onum[H];
                }
                
                Final[i] = total;
                
            }
            Console.Clear();
            foreach(int F in Final)
            { Console.WriteLine(F); }
        }
    }
}
```

## OX퀴즈
  - OX가 주어질때 O는 연속된 O의 갯수만큼 증가된 횟수만큼의 합, X는 0점, O를 초기화합니다.
  - 입력 : 첫째줄에 총진행할 갯수 N이 주어집니다. 2번째줄부터는 N개 만큼의 OX 테스트 문의 반복입니다. 
  - 조건 
      - 먼저 입력값 반복할 횟수를 받아줍니다. 
      - 2번쨰부터 테스트를 해야하는 데이터를 받아준뒤 바로 테스트에 사용할 데이터로 가공해줍니다.
      - 가공된 데이터를 이용해서 주어진 방식되로 점수를 구해줍니다<BR>
  - 출력 : 구해진 점수를 출력해줍니다.<br><br>

가장 먼저 반복횟루를 알려주는 N을 받아줍니다. N을 이용해서 반복횟수를 알게되었으니, 이를 통해 반복문을 준비해줍니다.

2번째 입력값은 OX로 구성된 Sting 값이 들어옵니다. String값이 공백이 없으니, 한자리로만 이루어진 Charactor로 변환해줍니다.
Charactor로는 한 String이라도 여러개의 Char로 구성되어 있으므로 Char를 집합으로 선언해주고, <mark style='background-color: #dcffe4'>.ToCharArray()를 통해 String을 가공해줍니다.</mark>

O가 연속될수록 숫자가 늘어나고 X나 나올시 초기화 됩니다.
이 두가지 조건을 이용해서 if 조건문을 작성해 줍니다.
만약 X가 나오면 주어진 카운트가 0으로 초기화 시키겠습니다.
그리고 연속되서 O가 나오게 되면 카운트는 1씩 증가합니다.
이를 위해 카운트를 해줄 num을 선언해 주겠습니다. num은 O 반복에 따라 1씩 증가하고, X가 나오면 0으로 초기화됩니다.
하지만 num만 있다면, 점수 총 합계를 알수도 없고, 0에서 초기화 되니 숫자가 세어지지 않을겁니다. 
따라서 따로 점수를 보관해줄 Onum[]에 O가 반복해서 증가할때마다 저장해두겠습니다.

이제 공식을 만든다면, 일단 char집합의 갯수만큼 반복해야지 OX 전체를 체크하게 될것이므로 이를 기반으로 반복문을 만들어 줍니다.
처음 if문에서는 char가 X라면 num을 초기화 해주고 X는 0점이므로 Onum에다가는 0을 저장해둡니다.

두번쨰 else에서는 O가 입력될시 num에 1을 추가해준 뒤, 그 숫자를 Onum에다가 저장해줍니다. 
이러면 Onum에 저장되게 됩니다.

마지막으로, 이제 모든값을 더해준뒤 결과를 출력해줍니다. 모든값을 더해주기 위해 total을 선언해준뒤 for반복문을 통해서 Onum의 갯수만큼 Onum을 더해주면 출력해주어야할 Total값이 나오게 됩니다.<mark style='background-color: #dcffe4'> 이 Total값을 출력해 주면됩니다. 전체 반복문이 1번 계산완료할떄마다 출력해주어도 되고, 저처럼 따로 Total을 Final에 저장해두었다가 마지막에 한번에 출력해주어도 됩니다.</mark>