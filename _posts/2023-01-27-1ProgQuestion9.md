---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 팩토리얼
date:   2023-01-25
description: about Programmers Question(08)
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
sitemap:
  changefreq: daily
  priority : 1.0
---

---
## Swift 프로그래머스 팩토리얼
---


```swift
import Foundation

func solution(_ n:Int) -> Int {
    var num = 1
    var answer = 0
    for i in 1...n{
        num *= i
        if num == n {
            answer = i
            break
        }
        else if num > n {
            answer = i - 1
            break
        }
    }
    return answer
}
```