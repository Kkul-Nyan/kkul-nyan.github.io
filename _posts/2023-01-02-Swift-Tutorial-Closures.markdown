---
layout: post
title:  Swift Closure
date:   2022-12-31
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Closure
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 클러저의 정의 및 특징
  - 클로저는 코드블럭으로 C와 Objective-C의 블록과 다른 언어의 람다와 비슷합니다.
  - 어떤 상수나 변수의 참조를 캡처해 저장할 수 있습니다. Swift는 이 캡처와 관련된 모든 메모리를 알아서 처리해줍니다.
  - 문맥에서 인자타입과 반환타입을 추론합니다.
  - 단일 표현 클로저에서의 암시적 반환이 가능합니다.
  - 축약된 인자이름을 사용할수 있습니다.
  - 후위 클로저 문법을 사용 가능합니다.

### 클로저의 형태
   - 클로저는 세가지 형태중 하나를 갖습니다
   1. 전역 함수 : 이름이 있고 어떤 값도 캡처하지 않은 클로저
   2. 중첩 함수 : 이름이 있고 관련된 함수로 부터 값을 캡처 할수 있는 클로저
   3. 클로저 표현 : 경량화 된 문법으로 쓰여지고 관련된 문액으로부터 값을 캡처할수 있는 이름이 없는 클로저.

### 클로저 표현
   - 클로저 표현은 인라인클로저를 명확하게 표현하는 방법으로 문법에 초첨이 맞춰져있습니다.
   - 코드의 명확성과 의도를 잃지 않으면서도 문법을 축약해 사용할수 있는 문법의 최적화 방법을 제공합니다.
   - 단, 람다 등 문법의 축약한것이기 때문에 당연히 축약시키지않은 일반식에 비해 모든 원소를 전부 순회하는 경우는 조금 느릴 수 밖에 없습니다.

#### 정렬메소드(The Sorted Method)
   - Swift의 표준 라이브러리에 sorted(by:)라는 알려진 타입의 배열값을 정렬하는 메소드를 제공합니다.
   - by에 어떤방법으로 정렬을 수행할지 기술한 클로저를 넣으면 그 방법되로 정렬된 배열을 얻을수 있습니다.
   - sorted(by:) 메소드는 2개의 인자를 갖는 클로저를 인자로 사용합니다.

```swift
let animals = ["cat", "dog", "bird", "hamster", "mause"]

func backward(_ s1: String, _ s2: String) -> Bool{
    return s1 > s2
}
var reversedNames = animals.sorted(by: backward)
print(reversedNames)
```
   - 여기서 s1 < s2 로 변경되게 되면 a,b,c,순으로 정렬되게됩니다.

#### 클로저 표현 문법(Closure Expression Syntax)
   - 일반적인 클로저의 형태는  {(parameters)-> return type in statements}입니다.
   - 인자로 넣을 parameters 인자값으로 처리할 내용을 기술하는 statements 그리고 return type입니다.
   - 함수형이 아닌 인자들로 구성된 방식을 사용 할수 있습니다. (String, String) throws -> Bool code
   - 인자로 구성된 클로저를 인라인 클로저라 부릅니다. 클로저의 몸통은 in 키워드 다음에 시작됩니다.

```swift
var reversedAnimals = animals.sorted(by:{ (s1: String,s2: String) -> Bool in return s1 < s2})
print(reversedAnimals)
```

#### 문맥에서의 타입 추론(Inferring Type From Context)
   - 클로저에서는 s1: String같이 타입을 알려주는 String을 생략할수 있습니다.
   - 가독성과 코드의 모호성이 생기기 때문에, 타입을 명시할 수도 있습니다. 선택사항입니다.
   - 만약 혼자 하는 작업이라면 많은부분을 생략하고, 자기스타일에 맞게 편하게 작업하면됩니다.

```swift
var reversedAnimals = animals.sorted(by:{ (s1,s2) -> Bool in return s1 < s2})
print(reversedAnimals)

var reversedAnimals = animals.sorted(by:{ (s1,s2) in return s1 < s2})
print(reversedAnimals)
```

#### 단일 표현 클로저에서의 암시적 반환(Implicit Return from Single-Express Closure)
   - 단일 표현 클로저에서는 반환키워드를 생략할수 있습니다.
   - 이렇게 표현해도 모호성이 없기 때문에 가능합니다. s1과 s2를 인자로 받아 비교한 결과값을 반환하는것입니다.

```swift
var reversedAnimals = animals.sorted(by:{ (s1,s2) in s1 < s2})
print(reversedAnimals)
```

#### 인자 이름 축약 (Shirthand Arguments Name)
   - 인라인 클로저에 자동으로 축약 인자 이름을 제공합니다.
   - 이 인자를 사용하면 인자 값을 순서대로 $0,$1,$2 등으로 사용 할수 있습니다.
   - 축약 인자 이름을 사용하면 인자 값과 그 인자로 처리할 때 사용하는 인자가 같다는 것을 알기 때문에 궂이 입력 인자를 적지 않아도 되고 따라서 In 역시 생략 할수 있습니다.

```swift
var reversedAnimals = animals.sorted(by: {$0 < $1})
print(reversedAnimals)
```

#### 연산자 메소드(Operator Method)
   - Swift의 String 타입 연산자에는 String끼리 비교 할수 있는 비교 연산자(>)를 구현해 두어있습니다.

```swift
var reversedAnimals = animals.sorted(by: <)
print(reversedAnimals)
```

### 후위 클로저(Trailing Closure)
   - 함수의 마지막 인자로 클로저를 넣고 그 클로저가 길다면 후위 클로저를 사용할수 있습니다.
   - func funcName (closure:() -> return){ func body } 이지만 클로저에 넣을게 많다면
   - func funcNAme (closure:{closure body}) 로 가능합니다. 
   - 함수의 마지막 인자가 클로저이고 후의 클로저를 사용하면 ()를 생략 가능합니다.

```swift
var reversedAnimals = animals.sorted(){$0 < $1}
print(reversedAnimals)

var reversedAnimals = animals.sorted{$0 < $1}
print(reversedAnimals)

//페이지 예제
let digitNames = [
    0: "Zero", 1: "One", 2: "Two",   3: "Three", 4: "Four",
    5: "Five", 6: "Six", 7: "Seven", 8: "Eight", 9: "Nine"
]
let numbers = [16, 58, 510]
let strings = numbers.map { (number) -> String in
    var number = number
    var output = ""
    repeat {
        output = digitNames[number % 10]! + output
        number /= 10
    } while number > 0
    return output
}
print(strings)
//digitNames[number % 10]!에 뒤에 느낌표(!)가 붙어있는 것은 사전(dictionary)의 subscript는 옵셔널이기 때문입니다.
```

### 값 캡처(Capturing Value)
   - 클로저는 특정 문맥의 상수나 변수의 값을 캡처 할 수 있습니다.
   - 캡처란 원본 값이 사라져도 클로저는 그값을 활용할수 있다는 의미입니다.
   - 가장 단순한 형태는 중첩함수 이며, 이는 함수의 body에서 다른 함수를 다시 불러오는 형태로 된 함수 입니다.
   - 캡처된 값은 사용되지 않으면 제거 하는등 관련된 메모리 관리를 알아서 합니다.

### 클로저는 참조 타입 (Closure Are Reference Type)
   - 함수와 클로저를 상수나 변수에 할당할 때 실제로는 상수와 변수에 해당 함수나 클로저의 참조가 할당 됩니다.
   - 그래서 만약 한 클로저를 두 상수나 변수에 할당하면 그 상수나 변수는 같은 클로저를 참조하고 있습니다.
   - C나 C++의 포인터를 저장하는 부분과 같다고 생각하면됩니다.

### 이스케이핑 클로저(Escaping Closure)
   - 클로저를 함수의 파라미터로 넣어 사용할때, 함수 밖에서 실행되는 클러저에는 파라티머 타입앞에 @escaping 이라는 키워드를 명시해야합니다.
   - @escaping을 사용하는 클러저에서는 self를 명시적으로 언급해야합니다.

### 자동클로저(AutoClosure)
   - 자동클러저는 인자 값이 없으며 특정 표현을 감싸서 다른 함수에 전달인자로 사용할수 있습니다.
   - 자동클러저는 클로저를 실행하기 전까지 실제 실행이 되지 않습니다. 
   - 복잡한 연산을 하는데 유용합니다.
   - 5번째 스크립트가 작동하고나서야 비로서 animal[0]이 제거됩니다. 

```swift
var animals = ["cat", "dog", "bird", "hamster", "mause"]
print(animals.count)
let customerProvider = {animals.remove(at: 0)}
print(animals.count)
print(customerProvider())
print(animals.count)
```