---
layout: post
title:  Swift 프로그래머스 7의 개수
date:   2023-02-06
image: Swift_logo.jpg
tags: [Swift]
---

---
## Swift 프로그래머스 7의 개수
---

```swift
import Foundation

func solution(_ array:[Int]) -> Int {
    var str = ""
    var count = 0
    for i in 0..<array.count {
        str.append(String(array[i]))
    }
    for j in str {
        if j == "7" {
            count += 1
        }
    }
    return count
}
```

7의 개수만 확인하면 되는 문제입니다.
주어진 집합을 for반복문을 통해 하나의 String으로 모아줍니다<br>
다른 for반복문을 통해 str 문자열을 접근하여, 문자열 "7"과 해당 문자열이 동일하다면
카운트가 1씩 증가하게 해주었습니다. 만일 문자열 "7"이 없다면 0이 나오게 되고,
집합안에 7이 존재한다면 7의 개수만큼 카운트가 증가하게됩니다.
