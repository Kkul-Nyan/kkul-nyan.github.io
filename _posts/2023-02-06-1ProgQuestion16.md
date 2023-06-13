---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 이진수 더기
date:   2023-02-06
description: about Programmers Question(15)
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
## Swift 프로그래머스 이진수 더하기
---

```swift
import Foundation

func solution(_ bin1:String, _ bin2:String) -> String {
    let num1 = Int(bin1, radix: 2)!
    let num2 = Int(bin2, radix: 2)!
    let answernum =  num1 + num2
    var answer = String(answernum, radix: 2)

    return "\(answer)"
}
```