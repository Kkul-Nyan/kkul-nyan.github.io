---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 가까운 수
date:   2023-01-25
description: about Programmers Question(10)
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift 프로그래머스 가까운 수
---

```swift
import Foundation

func solution(_ array:[Int], _ n:Int) -> Int {
    var beforeanswer = [Int]()
    var num = [Int]()
    for i in 0..<array.count {
        num.append(abs(array[i]-n))
    }
    var min =  num.sorted(by: <)
    for j in 0..<num.count {
        if abs(array[j]-n) == min[0] {
            beforeanswer.append(array[j])
        }
    }
    var answer = beforeanswer.sorted(by: <)
    return answer[0]
}
```

