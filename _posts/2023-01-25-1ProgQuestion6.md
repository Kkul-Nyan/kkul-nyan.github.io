---
layout: post
title:  Swift 프로그래머스 입문(5)
date:   2023-01-25
image: Swift_logo.jpg
tags: Swift
---

---
## Swift 프로그래머스 입문(5)
---

### 41. 세균 증식
```swift
import Foundation

func solution(_ n:Int, _ t:Int) -> Int {
    var total = n
    for _ in 1...t{
        total *= 2
    }
    return total
}
```
### 42. 대문자와 소문자
```swift
import Foundation

func solution(_ my_string:String) -> String {
    var result = ""
    for i in my_string{
        var check = String(i)
        result += (check == check.lowercased()) ? check.uppercased() : check.lowercased()
    }
    return result
}
```
### 43. n의 배수 고르기
```swift
import Foundation

func solution(_ n:Int, _ numlist:[Int]) -> [Int] {
    var number = [Int]()
    for i in numlist {
        if i % n == 0{
            number.append(i)
        }
    }
    return number
}
```
### 44. 암호 해독
```swift
import Foundation

func solution(_ cipher:String, _ code:Int) -> String {
    var checkNumber = cipher.count / code
    let cip = [Character](cipher)
    var new = ""
    for i in 1...checkNumber{
        var point = i * code
        new += String(cip[point-1])
    }
    return new
}
```
### 45. 가위 바위 보
```swift
import Foundation

func solution(_ rsp:String) -> String {
    var base = [Character](rsp)
    var str = ""
    for i in base {
        switch i {
        case "0":
            str.insert("5", at: str.endIndex)
        case "2":
            str.insert("0", at: str.endIndex)
        case "5":
            str.insert("2", at: str.endIndex)
        default:
            continue
        }
    }
    return str
}
```
### 46. 직각삼각형 출력하기
```swift
import Foundation

let n = readLine()!.components(separatedBy: [" "]).map { Int($0)! }
var number = [String]()
var star = ""
for i in 1...n[0] {
    star += "*"
    number.append(star)
    print(number[i-1])
}

```
### 47. 문자열 정렬하기 (1)
```swift
import Foundation

func solution(_ my_string:String) -> [Int] {

    let numbers = my_string.filter{$0.isNumber}.sorted()
    let str = numbers.map{ String($0) }
    let num = str.map{ Int($0)! }

    return num
}
```
### 48. 주사위의 개수
```swift
import Foundation

func solution(_ box:[Int], _ n:Int) -> Int {
    var new = [Int]()
    for i in box {
        new.append(i/n)
    }
    var result = new[0] * new[1] * new[2]
    return result
}

```
### 49. 가장 큰 수 찾기
```swift
import Foundation

func solution(_ array:[Int]) -> [Int] {
    var sort = array.sorted()
    var result = 0
    for i in 0..<array.count {
        if array[i] == sort[sort.endIndex-1]{
            result = i
        }
    }
    return [sort[sort.endIndex-1], result]
}
```
### 50. 배열 회전시키기
```swift
import Foundation

func solution(_ numbers:[Int], _ direction:String) -> [Int] {
    var checker = direction == "right" ? true : false
    var number = [Int](repeating: 0, count: numbers.count)
    if checker {
        for i in 0..<numbers.count{
            if i + 1 == numbers.count {
                number[0] = numbers[number.count - 1]
            }
            else{
                number[i+1] = numbers[i]
            }
        }
    }
    else {
        for j in 0..<numbers.count {
            if j == 0 {
                number[number.count - 1 ] = numbers[0]
            }
            else {
                number[j - 1] = numbers[j]
            }
        }
    }
    return number
}
```