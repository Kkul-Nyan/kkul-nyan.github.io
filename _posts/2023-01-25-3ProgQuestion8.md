---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 A로 B 만들기
date:   2023-01-25
description: about Programmers Question(07)
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
## Swift 프로그래머스 A로 B 만들기
---

```swift
import Foundation

func solution(_ before:String, _ after:String) -> Int {
    let str1 = before.sorted()
    let str2 = after.sorted()
    var answer = 0
    if str1 == str2 {
        answer = 1
    }
    else {
        answer = 0
    }
    return answer
}
```

A로 B를 만들수 있는 경우는 A와 B의 요소들이 모두 같을 때 입니다. A와 B의 요소의 갯수는 동일 합니다.
단순히 비교하게 되면, A와 B의 요소중 B에 2개가 있고 A에 하나만 있어도 모두 있다고 판단될수 있습니다.
따라서, <mark style='background-color: #dcffe4'>sort를 이용해서 차순 정리를 해줍니다. 두개가 동일한 요소를 지니고있다면 차순정리를 하게되면
A,B 요소들은 모두 동일한 인덱스에 동일한 요소가 있다는 의미입니다.</mark>
즉, A와 B의 sort가 동일 하다는 의미입니다. 요소하나하나를 비교할 필요없이 
if기정법을 동해 A.sort와 B.sort가 동일하다면 1을 반환, 다르다면 A로 B를 만들수없으므로 0을 반환해 줍니다.