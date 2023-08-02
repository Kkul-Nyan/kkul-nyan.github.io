---
layout: post
title:  Swift 프로그래머스 외게어 사전
date:   2023-02-24
image: Swift_logo.jpg
tags: Swift
---

---
## Swift 프로그래머스 외계어 사전
---

```swift
import Foundation

func solution(_ spell:[String], _ dic:[String]) -> Int {
    var count = 0
    var answer = 2
    for i in 0..<dic.count {
        for k in spell{
            var check = dic[i].contains(Character(k))
            if check == true{
                count += 1
            }
        }
        if count == spell.count {
            answer = 1
        }
        count = 0
    }
    
    return answer
}
```

contains를 포함하면 쉬운 문제입니다.<br>
첫 번째 for반복문을 통해 dic의 개수 만큼 반복해서 모든 dic을 확인 하는 과정입니다.<br>
두 번째 for반복문의 경우, contains를 통해 spell을 dic이 포함하는지 확인합니다.<br>
그러나 문제는 하나 포함하고 다음꺼는 포함안하면 결국 false로 결국 하나하나 체크하는것뿐입니다.<br>
따라서, 그 체크 상황을 정리해줄 count변수를 사용했습니다.<br>
예를들어, 주어진 spell이 3개인 상황에서 dic[0]이 spell[0],spell[1],spell[2]을 다포함한 경우만 count 3이고 이는 spell.count와 동일합니다.<br><br>
이경우만 answer에서 1로 반환해주고, 기본반환값은 2로 설정해서 따로 다 포함된경우가 아니면 2를 반환하게 해주었습니다.<br>