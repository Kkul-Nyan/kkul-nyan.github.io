---
layout: post
title:  Swift Enumeration
date:   2022-12-31
description: about Enumeration
image: Swift_logo.jpg
tags: Swift
sitemap:
  changefreq: daily
  priority : 1.0
---

---
## Swift Enumeration
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 열거형(Enumeration)
   - 열거형은 관련된 값으로 이루어진 그룹을 공통의 형으로 선언하는 것입니다.
   - 열거형은 1급 클래스형(first-class type)이어서 계산된 프로퍼티를 제공하거나 초기화를 지정하거나, 초기 선언을 확장해 사용할수있습니다.
   - 열거형은 유니티 C#에서도 많이 사용됩니다. 유저데이터라거나, 아이탬타입 관리등에서 자주사용했었습니다.
   - Swift의 열거형은 case별로 integer값을 할당하지않습니다. case별로 암시적으로 0,1,2...같은 값을 가지지 않는다는 의미입니다.
   - ,를 통해 구분해서 한줄에 적을수 있습니다
   - 각 열거형은 새로운 type을 정의합니다. 형의 이름은 대문자로 시작해야합니다.

#### 열거형 문법(Enumeration Syntax)
   - enum 키워드를 사용해 열거형을 정의합니다
   - enum 이름 { enumeration definition } 형태입니다

```swift
enum CompassPoint {
    case north
    case south
    case east
    case west
}
enum AminalType {
    case mammalia, Pisces, Reptilia, Aves, Tetrapoda, Osteichthyes, Chondrichthyes, Placodermi
}
var cat = AminalType.mammalia
print(type(of: cat))
```

#### Switch 구문에서 열거형 값 매칭하기(Matching Enumeration Value with a Switch Statement)
   - 각 열거형 값을 Switch 문에서 매칭 할수 있습니다.
   - switch문은 반드시 모든 열거형의 모든 case를 완전히 포함해야합니다.
   - 완전히 포함시키 힘들경우 default를 사용할수 있습니다.

```swift
var whatisthisAnimal = AminalType.Pisces
switch whatisthisAnimal {
case .mammalia:
    print("Dog","Cat")
case .Pisces:
    print("fish")
default:
    print("We finish soon")
}
```

#### 관련 값 (Associated Value)
   - 열거형의 각 custom type의 추가적인 정보를 저장할수 있습니다.
   - 예를들어, 타입을 제한하는등이 있습니다.
   - Switch와 혼용해서 더다양하게 사용할수있습니다(변수,상수로선언)

```swift
enum Barcode {
    case upc (Int,Int,Int,Int)
    case qrcode (String)
}
var clothBarcode = Barcode.upc(4,42553, 64564, 3)
print(clothBarcode)

enum Sbarcode{
    case upc (String,Int,String,Int)
}
var gameboard = Sbarcode.upc("XXbox", 400, "Mico", 210601 )
switch gameboard {
case .upc(var productname, var pruductprice , var barcodenumber, var madeday):
    print("UPC : \(productname) and \(pruductprice), \(barcodenumber), \(madeday)")
//case var .upc ( productname,  pruductprice ,  barcodenumber,  madeday): 처럼 사용도 가능합니다.
}
```

#### Raw 값 (Raw Value)
   - case에 raw값을 지정할수 있습니다.
   - String, Charactor, Integer, Float등의 형을 사용할 수 있습니다. 
   - Raw 값은 유일한 값으로 중복되어서는 안됩니다.
   - 암시적으로 Raw값을 할당할수도 있습니다.
   - raw값은 rawValue 프로퍼티를 사용해 접근할수 있습니다.
   - raw값을 이용해 열거형 변수를 초기화 할 수 있습니다. 6번째줄은 rawValue: 6을 기준으로 열거형 변수의 초기 값으로 지정합니다.

```swift
enum AminalType:Int {
    case mammalia = 1, Pisces, Reptilia , Aves , Tetrapoda, Osteichthyes, Chondrichthyes, Placodermi
}
var cat = AminalType.mammalia
print(cat.rawValue)
let Bonyfish = AminalType(rawValue: 6)
```

#### 재귀 열거자 (Recursive Enumeration)
   - 다른 열거 인스턴스를 관계 값으로 갖는 열거형 입니다. case앞에 indirect를 붙여 표시합니다.
   - 모든 case에 indirect를 붙여야 한다면, enum 키워드앞에 indirect를 표시합니다.

```swift
indirect enum numbers {
    case number(Int)
    case addition(numbers, numbers)
    case minus(numbers, numbers)
}
let five = numbers.number(5)
let four = numbers.number(4)
let sum = numbers.addition(five, four)
let minus = numbers.minus(five, four)

func evaluate(_ expression: numbers) -> Int {
    switch  expression {
    case let .number(value):
        return value
    case let .addition(left, right):
        return evaluate(left) + evaluate(right)
    case let .minus(left, right):
        return evaluate(left) * evaluate(right)
    }
}

print(evaluate(sum))
```