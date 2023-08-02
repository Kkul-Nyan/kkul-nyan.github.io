---
layout: post
title:  Swift Control Flow
date:   2022-12-31
image: Swift_logo.jpg
tags: [Swift]
---

---
## Swift Control Flow
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### For-In 문(For-In Loop)
   - For-In Loop는 속칭 반복문입니다. C#에 foreach반복문과 비슷하다고 느꼈습니다.
   - 배열, 숫자, 문자열을 순서대로 순회(iterate)하기 위해 사용합니다.
   - for 공식에서만사용할 변수명 in 순회할대상 으로 이루어져있습니다.
   - Dictionary에서 구성된 key-value으로 구성된 튜플을 순회하며 제어할수 있습니다
   - for-in을 순서대로 제어할 필요가없다면, 변수자리에 _키워드를 사용 할 수도있습니다.

```swift
let playerID = ["ABC", "Cat", "Dog", "Cola","Cake"]
for name in playerID {
    print("Hello New friend \(name)!")
}

let playerNumber = ["ABC": 1,"Cat": 4, "Dog": 32, "Cola": 3, "Cake": 10]
for (playername, playernumber) in playerNumber{
    print("Hello, \(playernumber) of \(playername)")
}

let base = 10
let power = 3
var answer = 1
for _ in 1...power{
    answer *= base
}
print(answer)
```

### While문(While Loop)
   - Swift에서는 while과 repeat-while  두 가지의 while문을 지원합니다.

#### while
   - 조건(condition)이 거짓(false)일 때까지 구문을 반복합니다.

```swift
var cat = 1
var dog = 10
while cat < dog{
    cat += 1
    print("Catcount is \(cat)")
}
```

#### Repeat-while
   - C#의 do-while과 비슷합니다.
   - 최소 한번 이상 실행하고 while처럼 조건이 거짓일 떄까지 반복합니다.

```swift
var cat = 1
var dog = 10
repeat{
    cat += 1
    print("Catcount is \(cat)")
} while cat > dog
```

### 조건적 구문(Conditional Statement)
   - C#에서 조건문으로 배운 형식입니다.
   - Swiftdㅔ서는 if와 switch 2가지의 조건 구문을 제공합니다.

#### if문
   - if, else if, else로 조건에 맞게 결과값을 도출할수 있습니다.
   - if만 사용하거나, if,else if만 사용하거나, if else등 if외에는 필요에따라 사용하기도 안하기도 해도됩니다.
```swift
var QRchecker = false
var login = false
if QRchecker && login == false {
    print("Access Deny")
}
else if QRchecker || login == false {
    print("Try Again")
}
else {
    print("Welcome")
}
```

#### Switch
   - Switch 문은 case에 따라 원하는 조건을 작성하고, 거기에 맞는 결과값을 도출해냅니다.
   - swith 입력될 조건 {구문 case: default:}입니다.
   - C와 Objective-C와는 달리 암시적인 진행을 사용하지 않는다고합니다. 구문이 기본적으로 모든 case를 순회하여 default를 만날떄까지 진행합니다. 즉, 유니티 C#에서 While문을 적을 때, 무조건 참인 조건을 걸고 break로 구문을 빠져나오듯이, C나 Objective-C에서는 case에 break를 이용해서 구문을 빠져나와야 쓸데없이 default까지 구문이 가동되는것을 막을수 있지만, Swift의 Switch에서는 case에 break를 걸지 않아도, 알아서 맞는 case를 만나면 자동으로 swith구문을 빠져나오게굅니다. C#에서도 swift와 동일해서 처음에 헷갈렸던 부분입니다.
   - case 안에는 최소 하나의 실행구문이 반드시 있어야합니다.
   - case 안에는 ,로 구분해서 복수의 조건을 혼합 사용할수 있습니다.
   - case부터 조사해서 내려가므로 default는 맨 마지막에 작성해야합니다.

``` swift
var optionbutton: Character = "f"
switch optionbutton {
case "a":
    print("Choose size of Font")
case "b":
    print("Choose mouse speed")
case "e":
    print("Exit Program")
case "f","g":
    print("Choose your Charactor")
default:
    print("Wrong Button")
}
```

#### 인터벌매칭 (Interval Matching)
   - 숫자의 특정 범위를 조건으로 사용할수 있습니다

```swift
var yourPoints = 45
switch yourPoints{
case 0..<30:
    print("Too Bad. Try Again")
case 30..<60:
    print("Bad")
case 60..<90:
    print("Good")
default:
    print("Your Great")
}
```

#### 튜플(Tuple)
   - 튜플을 조건으로 사용할수 있습니다.

```swift
var winlose = (1, 0)
switch winlose{
case (1, _):
    print("Normal")
case (_, 1):
    print("Normal")
case (1, 1):
    print("Winner")
default:
    print("Loser")
}
```

#### 값바인딩(Value Bindings)
   - 특정 변수를 각각 다른 case에서 정의하고 그정의된 상수,변수를 또다른 case에서 사용할수 있습니다.

```swift
var LuckeyNumbers = (0, 2)
switch LuckeyNumbers {
case (let x, 0):
    print("LuckyNumber is only \(x)")
case (0, let y):
    print("LuckyNumber is only \(y)")
case let (x, y):
    print("LuckyNumber is \(x) and \(y)")
}
```

#### where문을 사용가능합니다
   - Switch문 내에 case에서 where문을 사용할수 있습니다.
   - MYSQL에서도 공부했던 where절은 Swift에서도 조건을 추가하는데 사용합니다.

 ```swift
 var points = (50, 100)
switch points {
case let (x, y) where x > y:
    print("\(x) is Winner")
case let (x,y) where x < y:
    print("\(y) is Winner")
default:
    print("Same")
}
```  

### 제어 전송 구문 (Control Transfer Statement)
   - 코드의 진행을 계속 할지 말지를 결정하거나, 코드의 흐름을 바꾸기 위해 사용합니다.
   - continue : 현재 루프를 중지하고 다음 루프를 실행합니다.
   - break : 전체 루프를 중지합니다.
   - fallthrough : 조건이 완성되도, 무시하고 루프를 계속진행합니다. 조건이 맞는 case찾아도 break되지 않고 계속 진행시키는겁니다. case실행은 합니다.
   - return : 처음으로 돌아가서 다시 루프를 실행합니다.
   - throw : 결과값 유무에 상관없이 루프 실행을 멈춥니다.

#### 레이블구문 (Labeled Statements)
   - label 이름 while로 조건을 넣어 특정 구문을 실행하는데 사용합니다

```swift
label name: while condition{
    Statements
}
```
