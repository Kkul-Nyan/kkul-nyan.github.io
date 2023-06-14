---
layout: post
read_time: true
show_date: true
title:  Swift Operator
date:   2022-12-28
description: about Operator
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
## Swift Collection Operators
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

#### 할당연산자(Assignment Operator)
   -  = 입니다. == 와는 다릅니다.
   - 할당 연산자는 값을 초기화 시키거나 변경합니다. 상수, 변수 모두에 사용 가능합니다

```swift
let bbb = 10
var aaa = 5
aaa = bbb
print(aaa)
```

#### 사칙 연산자(Arithmetic Operators)
   - 덧셈(+), 뺄셈(-), 곱셈(*), 나눗샘(/) 입니다
   - 문자열끼리 합치기 위해 사용할수 있습니다

```swift
print(1 + 1)
print(10 - 5)
print(10 * 10)
print(10 / 5)
print("Animal" + " " + "cat")
```

#### 나머지 연산자(Remainder Operator)
   - %을 사용합니다
   - 나누기를 하면 /를 통해 몫을 구하지만 몫을 나누고 남은 나머지 값을 구하는데 사용합니다.

```swift
print( 9 % 4 )
```

#### 단항 음수 연산자(Unary Minus Operator)
    - 음수 연산자로 부호를 변경합니다.
    - 우리가 생각하는 그 '-'가 맞습니다.

```swift
let number  = 10
let minus = -number
print(minus)
```

#### 합성 할당 연산자(Compound Assignment Operators)
   - +=, -=와 같이 사칙연사자+할당연산자 형태 입니다
   - a = a + 1 같이 스스로를 사칙 연산하는것을 간단히 표현하기 위해 사용합니다.

```swift
var Pen = 100
Pen *= 3
print(Pen)
Pen /= 3
print(Pen)
Pen += 50
print(Pen)
Pen -= 50
print(Pen)
```

#### 비교 연산자(Comparison Operators)
   - 같다( a == b )
   - 같지않다( a != b )
   - 크다 ( a > b )
   - 작다 ( a < b )
   - 크거나 작다 ( a >= b )
   - 작거나 같다 ( a <= b )
   - if문 비교에서 많이 사용합니다. 제일많이 사용하는 연산자 인것 같습니다.
   
#### 삼항 조건 연산자(Ternary Conditional Operator)
   - 삼항연산자는  " ? : " 형태인데, 많이 사용하는 형식입니다.
   - 간단히 A? B : C라면, A가 true면 B, A가 false면 C라는 의미입니다. if문같은 조건문을 간단히 작성가능합니다.

```swift
var ABC = true
var DEF = 50
let Price = DEF + (ABC ? 100 : 0)
print(Price)
```

#### Nil 병합 연산자(Nil-Coalescing Operator)
   - A ?? B 형태를 가지고 있습니다
   - Optional A를 벗겨서(Unwrap) 만약 A가 nil인 경우 B를 반환합니다
   - 원형은 A != nil ? A! : B 입니다
   - 옵셔널 A가 nil이 아니면 a를 unwrap하고 만약 nil이면 nil이 아니라 B를 반환하라는 것입니다.

```swift
var PlayerName: String?
var usedPlayerName = "Please use other name"
var PlayerNameToUse = PlayerName ?? usedPlayerName
print(PlayerNameToUse)
```

#### 범위 연산자(Range Operator)
   - (a...b)의 형태로 시작과 끝의 숫자를 알려줍니다. a부터 시작해서 b까지라는 의미입니다. 
   - 처음 PlayGround에서 for-in loop 문에서 만났을 때, 색다른 모습에 당황했던 기억이있습니다.

```swift
for cookie in 1...5{
    print("cookie count is \(cookie)")
}
```

#### 반 닫힌 범위 연산자(Half-Open Range Operator)
   - A..<B 의 형태로 A부터 B보다 작을 때(미만)까지의 범위입니다. 즉 범위연산자는 B를 포합하지만, 반닫힌 범위 연산자는 B를 포함하지 않습니다. 
   - 간단하게 '미만'으로 이해하면 됩니다.
   - 보통 배열은 0부터 시작해서 범위연산자를 사용하면 -1 를 따로 해주는 번거로움이 있지만, 이를 사용하면 그런 번거로움이 없습니다.

#### 단방향 범위 (One-Side Ranges)
   - [a...], [...a]의 형태입니다.
   - 시작지점 이나 범위의 끝 부분만 지정하는 범위연산자입니다.
   - 시작지점만 지정해두었지만, 배열의 끝부분까지만 반복하는등 유용한 방안입니다.
   - 반 닫힌 범위 연산자와 함꼐 사용할수 있습니다.

```swift
var name:[String] = ["dog", "cat", "mause", "bird"]
for animal in name[0...]{
    print("\(animal) is Animal")
}
for animal1 in name[...1]{
    print("\(animal1) is animal")
}
for animal2 in name[..<1]{
    print("\(animal2) is animal")
}
```

#### 논리 연산자
   - Swift는 3가지 표준 논리 연산자를 지원합니다.
   - 논리부정 Not(!) => false를 의미합니다.
   - 논리 곱 And(&&) => 둘다 논리적으로 true어야합니다.
   - 논리 합 OR(||) => 둘중 하나만 true면 됩니다.
   - 논리 연산자는 2개이상 조합해서 사용할수 있습니다.
   - 논리 연산자는 수학식처럼 괄호를 통해 계산순서를 지정할수도 있습니다.

```swift
let usedPlayerName = "cat"
let usedPassword = 123123
var typedName = "cat"
var typedPassword = 123123
var nameAccess = false
var passwordAccess = false
var QRChecker = false

if !QRChecker {
    print("Check your QR or Use ID and Password")
}
else {
    print("WelCome QR")
}

if usedPlayerName == typedName{
    nameAccess = true
    if usedPassword == typedPassword{
        passwordAccess = true
    }
    else{       
        passwordAccess = false
    }
}
else{
    nameAccess = false
}

if nameAccess && passwordAccess {
    print("Welcome")
}
else if nameAccess || passwordAccess {
    print("Ckeck your ID or Password")
}
else {
    print("you can register our site")
}
```