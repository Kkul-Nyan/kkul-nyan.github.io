---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 k의 개수
date:   2023-02-01
description: about Programmers Question(10)
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift 프로그래머스 k의 개수
---

```swift
import Foundation

func solution(_ i:Int, _ j:Int, _ k:Int) -> Int {
    let startNum = i
    let endNum = j
    let checkNum = k
    var nums = [Int]()
    var str = ""
    var count = 0
    for i in startNum...endNum {
        nums.append(i)
    }
    for i in 0..<nums.count {
        str.append(String(nums[i]))
    }
    for i in str {
        if String(i) == String(checkNum) {
            count += 1
        }
    }
    return count
}
```