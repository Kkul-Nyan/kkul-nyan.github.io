---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 숨어있는 숫자의 덧셈 (2)
date:   2023-02-04
description: about Programmers Question(14)
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift 프로그래머스 숨어있는 숫자의 덧셈 (2)
---

```swift
import Foundation

func solution(_ my_string:String) -> Int {
    let numbers = my_string.split(whereSeparator:{!$0.isNumber})
    var answer = 0
    for i in numbers {
       answer += Int(i)!
    }
    print(numbers)
    
    return answer
}
```

처음 문제 풀이를 할때는 my_string.fliter를 통해 숫자만 뽑았지만, 그렇게 할 경우 2자리이상의 자연수를 한자리로만 인식해서
추가적인 작업이 필요했습니다. 따라서, split을 통해 Int값이 아닌 경우를 기준으로 나누어주었습니다.
숫자가 아닌 경우를 기준으로 나누었기때문에, 2자리수 이상의 자연수도 문제없게 되었습니다.