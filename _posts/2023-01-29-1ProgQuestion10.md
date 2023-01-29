---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 2차원으로 만들기
date:   2023-01-25
description: about Programmers Question(08)
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift 프로그래머스 2차원으로 만들기
---

```swift
import Foundation

func solution(_ num_list:[Int], _ n:Int) -> [[Int]] {
    let bn = num_list.count / n

    var count = 0
    var answer: [[Int]] = Array(repeating: Array(repeating: 0 ,count: n), count: bn)
    for i in answer.indices{
        for j in answer[i].indices {
            answer[i][j] = num_list[count]
            count += 1
        }
    }
    return answer
}
```