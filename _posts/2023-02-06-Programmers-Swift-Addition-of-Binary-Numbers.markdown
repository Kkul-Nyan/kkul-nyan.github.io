---
layout: post
title:  Swift 프로그래머스 이진수 더하기
date:   2023-02-06
image: Swift_logo.webp
tags: [Swift]
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