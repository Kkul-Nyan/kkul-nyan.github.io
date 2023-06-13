---
layout: post
read_time: true
show_date: true
title:  Swift 프로그래머스 입문(4)
date:   2023-01-24
description: about Programmers Question(04)
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
## Swift 프로그래머스 입문(4)
---

### 31. 배열 두 배 만들기
```swift
import Foundation

func solution(_ numbers:[Int]) -> [Int] {
    var num = [Int]()
    for i in 0..<numbers.count{
        num.append(numbers[i] * 2)
    }
    return num
}
```
### 32. 중앙값 구하기
```swift
import Foundation

func solution(_ array:[Int]) -> Int {
    var sortlist = array.sorted()
    var center = array.count / 2
    return sortlist[center]
}
```
### 33. 옷가게 할인 받기
```swift
import Foundation

func solution(_ price:Int) -> Int {
    var result = Double(price)
    if 100000 <= result && result < 300000{
        result = floor(result * (95 / 100))
    }
    else if 300000 <= result && result < 500000{
        result = floor(result * (90 / 100))
    }
    else if 500000 <= result{
        result = floor(result * (80 / 100))
    }
    return Int(result)
}
```
### 34. 순서쌍의 개수
```swift
import Foundation

func solution(_ n:Int) -> Int {
    var number = 0
    for i in 1...n {
        if n % i == 0 {
            number += 1
        }
    }
    return number
}
```
### 35. 배열의 유사도
```swift
import Foundation

func solution(_ s1:[String], _ s2:[String]) -> Int {
    var count = 0
    
    for i in 0..<s1.count{
        for j in 0..<s2.count{
            if s1[i] == s2[j]{
                count += 1
            }
        }
    }
    return count
}
```
### 36. 자릿수 더하기
```swift
import Foundation

func solution(_ n:Int) -> Int {
    var str = String(n)
    var numbers = [String]()
    var count: Int = 0
    for number in str{
        numbers.append(String(number))
    }

    for i in 0..<numbers.count{
        var counts = Int(numbers[i])
        count += counts!
    }
    return count
}
```
### 37. 문자열안에 문자열
```swift
import Foundation

func solution(_ str1:String, _ str2:String) -> Int {
    var result = 2
    if str1.contains(str2) {
        result = 1
    }
    return result
}
```
### 38. 숨어있는 숫자의 덧샘(1)
```swift
import Foundation

func solution(_ my_string:String) -> Int {
    var count = 0
    var str = my_string.filter({$0.isNumber})
    var char = [String]()
    for i in str{
        char.append(String(i))
    }
    for j in 0..<char.count {
        count += Int(char[j])!
    }
    return count
}
```
### 39. 개미 군단
```swift
import Foundation

func solution(_ hp:Int) -> Int {
    var left = hp
    var count = 0
    if (left / 5) != 0 {
        count += (left/5)
        left -= (5 * (left/5))
    }
    if (left / 3) != 0 {
        count += (left/3)
        left -= (3 * (left/3))
    }
    count += left
    return count
}
```
### 40. 모음 제거
```swift
import Foundation

func solution(_ my_string:String) -> String {
    var str = my_string.filter{ !["a","e","i","o","u"].contains($0)}
    return str
}

```