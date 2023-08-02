---
layout: post
title:  Swift 프로그래머스 입문(3)
date:   2023-01-21
image: Swift_logo.jpg
tags: [Swift]
---

---
## Swift 프로그래머스 입문(3)
---
### 21. 문자열 뒤집기
```swift
import Foundation

func solution(_ my_string:String) -> String {
    var string = ""
    for i in my_string{
        string.insert(i, at: string.startIndex)
    }
    return string
    
}
```
### 22. 짝수 홀수 개수
```swift
import Foundation

func solution(_ num_list:[Int]) -> [Int] {
    var base = 0
    var num = 0
    var num1 = 0
    for i in 0..<num_list.count{
        if base == num_list[i]%2 {
            num += 1
        }
        else {
            num1 += 1
        }
    }
    var num2 = [num,num1]
    return num2
}
```
### 23. 삼각형의 완성조건(1)
```swift
import Foundation

func solution(_ sides:[Int]) -> Int {
    var Total = 0
    var result = 1
    for i in 0..<sides.count{
        Total += sides[i]
    }
    for count in 0..<sides.count{
        if(Total - sides[count] <= sides[count])
        {
            result = 2
        }
    }
    return result
}
```
### 24. 특정 문자 제거하기
```swift
import Foundation

func solution(_ my_string:String, _ letter:String) -> String {
    var str = ""
    for i in my_string{
        if( letter != String(i) ){
            str.append(i)
        }
    }
    return str
}
```
### 25. 중복된 숫자 개수
```swift
import Foundation

func solution(_ array:[Int], _ n:Int) -> Int {
    var count = 0
    for i in 0..<array.count{
        n != array[i] ? (count += 0) : (count += 1)
    }
    return count
}
```
### 26. 피자 나눠먹기 (3)
```swift
import Foundation

func solution(_ slice:Int, _ n:Int) -> Int {
    return Int(ceil(Double(n)/Double(slice)))
}
```
### 27. 문자 반복 출력하기
```swift
import Foundation

func solution(_ my_string:String, _ n:Int) -> String {
    var str = ""

    for i in my_string{
        for _ in 0..<n {
            str.append(i)
        }
    }
    return str
}
```
### 28. 짝수는 싫어요
```swift
import Foundation

func solution(_ n:Int) -> [Int] {
    var odd = [Int]()
    for i in 1...n {
        if(i % 2 != 0){
            odd.append(i)
        }  
    }
    return odd
}

```
### 29. 제곱수 판별하기
```swift
import Foundation

func solution(_ n:Int) -> Int {
    var num = 2
    for i in 1..<n {
        if(i * i == n){
            num = 1
        }
    }
    return num
}
```
### 30. 편지
```swift
import Foundation

func solution(_ message:String) -> Int {
    return message.count * 2
}
```