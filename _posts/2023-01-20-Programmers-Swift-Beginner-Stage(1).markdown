---
layout: post
title:  Swift 프로그래머스 입문(1)
date:   2023-01-11
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift 프로그래머스 입문(1)
---

### 1.두 수의 차
```swift
import Foundation

func solution(_ num1:Int, _ num2:Int) -> Int {
    let num3 = num1 - num2
    return num3
}
```

### 2.숫자 비교하기
```swift
import Foundation

func solution(_ num1:Int, _ num2:Int) -> Int {
    var answer = num1 == num2 ? 1 : -1
    
    return answer
}
```
### 3.몫 구하기
```swift
import Foundation

func solution(_ num1:Int, _ num2:Int) -> Int {
    return num1/num2
}
```
### 4.두 수의 곱
```swift
import Foundation

func solution(_ num1:Int, _ num2:Int) -> Int {
    var answer = num1 * num2
    return answer
}
```
### 5.나이 출력
```swift
import Foundation

func solution(_ age:Int) -> Int {
    
    var answer = 2023 - age 
    return answer
}
```
### 6.나머지 구하기
```swift
import Foundation

func solution(_ num1:Int, _ num2:Int) -> Int {
    
    return num1 % num2
}
```
### 7.두 수의 합
```swift
import Foundation

func solution(_ num1:Int, _ num2:Int) -> Int {
    return num1 + num2
}
```
### 8.각도기
```swift
import Foundation

func solution(_ angle:Int) -> Int {
    var answer:Int
    if(angle > 0 && angle < 90 ) {answer = 1}
    else if(angle == 90 ) {answer = 2}
    else if(angle > 90 && angle < 180) {answer = 3}
    else {answer = 4}
    return answer
}
```
### 9.두 수의 나눗셈
```swift
import Foundation

func solution(_ num1:Int, _ num2:Int) -> Int {
    var num3 = Double(num1)
    var num4 = Double(num2)
    var num5 = floor((num3/num4) * 1000)
    return Int(num5)
}

```
### 10.짝수의 합
```swift
import Foundation

func solution(_ n:Int) -> Int {
    let num = n/2
    var num1 = 0
    var num2 = 0
    while(num1 < num){
        num1 += 1
        num2 += num1
    }
    var answer = num2 * 2
    return answer
}
```