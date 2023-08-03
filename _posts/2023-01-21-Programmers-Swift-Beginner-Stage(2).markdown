---
layout: post
title:  Swift 프로그래머스 입문(2)
date:   2023-01-21
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift 프로그래머스 입문(2)
---

### 11.배열의 평균
```swift
import Foundation

func solution(_ numbers:[Int]) -> Double {
    var sum: Double = 0
    for i in 0..<numbers.count{
        sum += Double(numbers[i])
    }
    var answer:Double = sum / Double(numbers.count)
    return answer
}
```
### 12.양꼬치
```swift
import Foundation

func solution(_ n:Int, _ k:Int) -> Int {
    var rampPrice = 12000
    var drinkPrice = 2000
    var anwser = (rampPrice * n) + (drinkPrice * k) - (drinkPrice * (n/10))
    return anwser
}
``` 
### 13.아이스 아메리카노
```swift
import Foundation

func solution(_ money:Int) -> [Int] {
    var num = money / 5500
    var num1 = money % 5500
    return [num, num1]
}
```
### 14.피자 나눠먹기(1)
```swift
import Foundation

func solution(_ n:Int) -> Int {
    return Int(ceil(Double(n)/7))
}
```
### 15.배열 원소의 길이
```swift
import Foundation

func solution(_ strlist:[String]) -> [Int] {
    var num = [Int]()
    for i in 0 ..< strlist.count{
        num.append(strlist[i].count)
    }
    return num
}
```
### 16.배열 뒤집기
```swift
import Foundation

func solution(_ num_list:[Int]) -> [Int] {
    var nums = [Int]()
    for i in 0 ..< num_list.count {
        nums.append(num_list[num_list.count - i - 1])
    }
    return nums
}
```
### 17.머쓱이보다 키 큰 사람
```swift
import Foundation

func solution(_ array:[Int], _ height:Int) -> Int {
    var big = 0
    for i in 0..<array.count{
        if(height < array[i])
        {
            big += 1
        }
    }
    return big
}

```
### 18.점의 위치 구하기
```swift
import Foundation

func solution(_ dot:[Int]) -> Int {
    var x : Bool = dot[0] > 0 ? true : false 
    var y : Bool = dot[1] > 0 ? true : false
    var result = 0
    switch (x,y){
    case (true, true):
        result = 1
    case(false, true):
        result = 2
    case(false, false):
        result = 3
    case(true, false):
        result = 4
    }
    return result
}
```
### 19.배열 자르기
```swift
import Foundation

func solution(_ numbers:[Int], _ num1:Int, _ num2:Int) -> [Int] {
    var num = [Int]()
    for i in num1...num2{
        num.append(numbers[i])
    }
    return num
}
```
### 20.최댓값 만들기
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