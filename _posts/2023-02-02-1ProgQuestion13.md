---
layout: post
title:  Swift 프로그래머스 진료순서 정하기
date:   2023-02-02
description: about Programmers Question(12)
image: Swift_logo.jpg
tags: Swift
sitemap:
  changefreq: daily
  priority : 1.0
---

---
## Swift 프로그래머스 진료순서 정하기
---

```swift
import Foundation

func solution(_ emergency:[Int]) -> [Int] {
    let sorted = emergency.sorted(by:>)
    var dic = [Int : Int]()
    
    for i in 0 ..< sorted.count {
        dic[sorted[i]] = i + 1
    }
    var answer = [Int]()
    for i in emergency{
        answer.append(dic[i]!)
    }
    return answer
}
```