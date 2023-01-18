---
layout: post
read_time: true
show_date: true
title:  프로그래머스 옹알이(1)
date:   2023-01-19
description: about Programmers Question
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## 프로그래머스 옹알이(1)
---

```swift
import Foundation

func solution(_ babbling:[String]) -> Int {

    var array = ["aya", "ye", "woo", "ma"]
    var count = 0
    var newarray = [String]()
    for i in 0..<array.count {
            for j in 0..<array.count {
                for k in 0..<array.count {
                    for a in 0..<array.count {
                        if i==j || j == k || k == i || i == a || j == a || k == a { //중복 제거
                            continue
                        }
                        newarray.append(array[i] + array[j] + array[k] + array[a])
                    }
                }
             }
         }
    for i in 0..<array.count {
            for j in 0..<array.count {
                for k in 0..<array.count {
                    if i==j || j == k || k == i { //중복 제거
                        continue
                    }
                    newarray.append(array[i] + array[j] + array[k])
                }
             }
         }
    for i in 0..<array.count {
            for j in 0..<array.count {
                if i==j { //중복 제거
                    continue
                }
                newarray.append(array[i] + array[j])
            }
         }
    for i in 0..<array.count{
        newarray.append(array[i])
    }
    for i in newarray{
        for j in babbling{
            if i == j{
                count += 1
            }
        }
    }
    return count
}
```

4개의 단어로 만들수 있는 경우의 수는 (4 * 3 * 2 * 1) + (4 * 3 * 2) + (4 * 3) + 4의 경우입니다. 
(4 * 3 * 2 * 1)과 (4 * 3 * 2)는 명백히 다릅니다. 4단어와 3단어 조합의 차이입니다.
이렇게 구할수 있는 경우의 수는 모두 64가지 입니다. 
for 반복문을 통해 4가지 조합, 3가지 조합, 2가지 조합을 구해준뒤, newarray에 모아주었습니다.
입력해서 들어온 babbling과 비교해서 babbling 인자가 64가지 경우와 동일하다면 count를 추가해서 최종적으로 발음할수 있는 숫자를 구해주었습니다.