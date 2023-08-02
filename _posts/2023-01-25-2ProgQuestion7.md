---
layout: post
title:  Swift 프로그래머스 입문(6)
date:   2023-01-25
image: Swift_logo.jpg
tags: Swift
---

---
## Swift 프로그래머스 입문(6)
---

### 51. 외계 행성의 나이
```swift
import Foundation

func solution(_ age:Int) -> String {
    var dic: [ Character : String ] = ["0" : "a", "1" : "b", "2" : "c", "3" : "d", "4" : "e", "5" : "f", "6" : "g", "7" : "h", "8" : "i", "9" : "j" ]
    var str = String(age)
    
    var result = ""
    for i in str {
        result.append(dic[i]!)
    }
    
    return result
}
```
### 52. 최댓값 만들기 (2)
```swift
import Foundation

func solution(_ numbers:[Int]) -> Int {
    var num = [Int]()
    for i in 0..<numbers.count{
        for j in 0..<numbers.count {
            if i != j {
                num.append( numbers[i] * numbers[j])
            }
        }
    }
    return num.max()!
}
```
### 53. 피자 나눠 먹기 (2)
```swift
import Foundation

func solution(_ n:Int) -> Int {
    let slice = 6
    let people = n
    var pizza = 0
    var find = false
    while (find == false){
        pizza += 1
        if ( 6 * pizza ) % n == 0 {
            find = true
        }
    }
    return pizza
}
```
### 54. 인덱스 바꾸기
```swift
import Foundation

func solution(_ my_string:String, _ num1:Int, _ num2:Int) -> String {
    var str = [Character](my_string)
    var keepNum = ""
    
    keepNum = String(str[num1])
    str[num1] = str[num2]
    str[num2] = Character(keepNum)
    
    var answer = ""
    for i in str {
        answer.append(String(i))
    }
    return answer
}
```
### 55. 약수 구하기
```swift
import Foundation

func solution(_ n:Int) -> [Int] {
    var num = [Int]()
    for i in 1...n {
        if (n % i) == 0 {
            num.append(i)
        }
    }  
    return num
}
```
### 56. 숫자 찾기
```swift
import Foundation

func solution(_ num:Int, _ k:Int) -> Int {
    var str = String(num)
    var char = [Character](str)
    var answer = -1
    for i in 0 ..< char.count {
        if k == Int(String(char[i]))! {
            answer = i + 1
            break
        }
    }
    return answer
}
```
### 57. 369게임
```swift
import Foundation

func solution(_ order:Int) -> Int {
    let char = [Character](String(order))
    var count = 0
    for i in char {
        switch i {
        case "3":
            count += 1
        case "6":
            count += 1
        case "9":
            count += 1
        default:
            continue
        }
    }
    return count
}
```
### 58. 문자열 정렬하기 (2)
```swift
import Foundation

func solution(_ my_string:String) -> String {
    var char = [Character](my_string)
    var str = [String]()
    for j in 0..<char.count {
        
        str.append(String(char[j]).lowercased())
        
    }
    
    var sort = str.sorted()
    var answer = ""
    for i in sort {
        answer.append(i)
    }
    return answer
}
```
### 59. 합성수 찾기
```swift
import Foundation

func solution(_ n:Int) -> Int {
    var answer = 0
    for i in 1...n {
        var count = 0
        for j in 1...i {
            if ( i % j) == 0{
                count += 1
            }
        }
        if count > 2 {
            answer += 1
        }
    }
    return answer
}
```
### 60. 모스부호 (1)
```swift
import Foundation

func solution(_ letter:String) -> String {
    
    let mose: (Dictionary) = [ ".-":"a","-...":"b","-.-.":"c","-..":"d",".":"e","..-.":"f", "--.":"g","....":"h","..":"i",".---":"j","-.-":"k",".-..":"l", "--":"m","-.":"n","---":"o",".--.":"p","--.-":"q",".-.":"r", "...":"s","-":"t","..-":"u","...-":"v",".--":"w","-..-":"x", "-.--":"y","--..":"z" ]
    
    var le = letter.split(separator: " ").map({ (substring) in return String(substring)})
    var answer = ""
    
    for i in le {
        answer.append(mose[i]!)
    }
    
    return answer
}
```