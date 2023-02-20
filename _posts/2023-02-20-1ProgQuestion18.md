---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 영어가 싫어요
date:   2023-02-20
description: about Programmers Question(17)
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift 프로그래머스 영어가 싫어요
---

```swift
import Foundation

func solution(_ numbers:String) -> Int64 {
    let english: [String: String] = ["zero": "0", "one": "1", "two": "2", "three": "3", "four": "4", "five": "5", "six": "6", "seven": "7", "eight": "8", "nine": "9" ]
    var result = numbers
    for i in english {
        result = result.replacingOccurrences(of: i.key, with: i.value)
    }
    return Int64(result)!
}
```

replacingOccurrences를 사용하면 간단하게 풀이가 가능한 문제입니다</br>


```swift
func replacingOccurrences(
    of target: String,
    with replacement: String
) -> String
```
target String을 replacement String으로 치환해줍니다.
즉, 바꾸고 싶은 대상을 target 여기서는 i.key값입니다. 바꾸는 기준을 replacement 여기서는 i의 키값에 대칭되는 value값입니다.
이를 통해, 키값에 맞게 밸류값으로 치환됩니다.