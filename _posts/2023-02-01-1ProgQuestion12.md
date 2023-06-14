---
layout: post
title:  Swift 프로그래머스 k의 개수
date:   2023-02-01
description: about Programmers Question(11)
image: Swift_logo.jpg
tags: Swift
sitemap:
  changefreq: daily
  priority : 1.0
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