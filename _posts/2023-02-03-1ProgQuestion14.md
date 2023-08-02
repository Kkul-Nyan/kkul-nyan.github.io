---
layout: post
title:  Swift 프로그래머스 한 번만 등장한 문자
date:   2023-02-03
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift 프로그래머스 한 번만 등장한 문자
---

```swift
import Foundation

func solution(_ s:String) -> String {
    var char = [Character]()
    var group = [Character]()
    var count = 0
    for i in s {
        char.append(i)
    }
    for j in 0..<char.count {
        for i in 0..<char.count {
            if char[i] == char[j] {
             count += 1
            }
        }
        if count == 1 {
            group.append(char[j])
        }
        count = 0
    }
    var sorted = group.sorted(by: <)
    var answer = ""
    for i in sorted {
        answer.append(String(i))
    }
    
    return answer
}
```