---
layout: post
title:  Swift Method
date:   2022-12-31
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Method
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 


### 매소드(Method)
   - 특정타입의 클래스, 구조체, 열거형과 관련된 함수를 메소드라 합니다.
   - 특정 타입의 인스턴스에서 실행할수 있는 메소드를 인스턴스 메소스, 특정형과 관련된 메소드를 타입 메소드라 합니다.
   - Swift에서는 클래스타입뿐만아니라 구조체, 열거형에서도 메소드를 선언해 사용할수 있습니다.

### 인스턴스메소드(Instance Method)
   - 특정 클래스, 구조체, 열거형의 인스턴스에 속한 메소드입니다. 
   - 인스턴스 내의 값을 제어하거나 변경할수 있습니다.
   - 인스턴스 메소드는 그 인스턴스가 속한 특정 타입의 인스턴스에서만 실행 가능합니다.
   - Simple 클래스의 func Sum()과 Minus()를 정의했고, result 프로퍼티를 변경하는 기능을 수행합니다.

```swift
class Simple {
    var result = 0
    func Sum(a: Int, b: Int) {
        result = a + b
    }
    func Minus(a: Int, b: Int) {
        if a > b {
            result = a - b
        }
        else {
            result = b - a
        }
    }   
}
var simple = Simple()
simple.Minus(a: 10, b: 4)
print(simple.result)
```

### self 프로퍼티(The Self Property)
   - 모든 프로퍼티는 암시적으로 인스턴스 자체를 의미하는 self 프로퍼티를 가지고있습니다.
   - 인스턴스 자체를 참조하는데 사용할수 있습니다.
   - 결국, 함수내의 result는 self.result의 약어입니다.
   - 단, 인자이름이 프로퍼티 이름과 동일한 경우는 프로퍼티에 self를 꼭적어 구분해주어합니다. 이름이 같은상황에서는 Swift에서 인자로 추정합니다.
   \* 인자란 func의 전달인자입니다. 

```swift
class Simple {
    var result = 0

    func Increase() {
        self.result += 1
    }
    func decrease() {
        result -= 1
    }
}

var simple = Simple()
simple.Increase()
print(simple.result)
```
#### 인스턴스 메소드 내에서 값 타입 변경(Modifyting Value Type from Within Instance Method)
   - 구조체와 열겨형 타입에서 기본적으로 값 타입의 프로퍼티를 변경할수 없습니다
   - mutating을 붙여주어 프로퍼티 변경이 가능해집니다.
   - mutating 이라는 키워드가 붙은 메소드에서는 계산이 끝난후, 원본 구조체에 그결과를 덮어 써서 변경합니다.

```swift
import Foundation

struct Simple {
    var result = 0

    mutating func Increase() {
        result += 1
        // 오류가 전혀없습니다. mutating을 통해 funcdㅣ result의 값을 변경할수 있기 때문입니다.
        // 단, 당연히 상수의 변경은 안됩니다.
    }
    func decrease() {
        result -= 1
        // 바로 오류가 생깁니다. Left side of mutating operator isn't mutable: 'self' is immutable
        // 내부 함수라 하여도 struct의 값을 변경할려고 하기때문입니다. mutable 
    }
    
}
```

#### Mutating 메소드 내에서 self 할당 (Assigning to Self Within a Mutating Method)
   - Mutating 메소드에서도 self 프로퍼티를 이용해 새로운 인스턴스를 생성할수 있습니다.

```swift
struct Simple {
    var result = 0

    mutating func Increase() {
        self.result += 1
    }
    mutating func decrease() {
        result -= 1
    }
    
}
var simple = Simple()
simple.Increase()
print(simple.result)
```

### 타입메소드(Type Method)
   - 타입 메소드는 특정 타입 자체에서 호출해 사용합니다.
   - 메소드 키워드 앞에 static 혹은 class 키워드를 추가하면 됩니다. 
   - static은 서브클래스에서 오버라이드 할 수 없고, class는 가능합니다.
   - dot 문법을 통해 호출 할 수 있습니다. 단, 타입이름에서 메소드를 호출해야합니다.
   - 타입이름에서 메소드를 호출해야하는게 단점같지만, 굳이 인스턴스를 만들필요없이 호출해서 쓸수 있는 편리함이있습니다.
   - 앞에서 static, class를 타입프로퍼티에서봤었습니다. 초기자가 없는 특징은 똑같습니다. 즉 내부 변수를 쓸수없습니다.

```swift
class Simple {
    static var result = 0
    var result1 = 0
    class func Increase() {
        result += 1
    }
    class func decrease() {
        self.result1 -= 1
    }
    
}
var simple = Simple()
Simple.Increase()
print(Simple.result)
```

   - var result 가 static 선언되었습니다. 만약 static으로 선언되지 않는다면 class func에서 불려쓰지 못합니다.
   - decrease에서는 오류가 생깁니다. static선언되지 않은 result1이기 때문에 self가 타입자기자신을 의미하는것이지 result를 의미하는것이 아닙니다.