---
layout: post
read_time: true
show_date: true
title:  Swift Initialization
date:   2022-12-31
description: about Initialization
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift Initialization
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 정의
   - 초기화는 클래스, 구조체, 열거형 인스턴스를 사용하기 위해 준비 작업을 하는 단계입니다.
   - 각 저장 프로퍼티의 초기값을 설정합니다.
   - 초기화 과정은 initalizer를 정의 하는것으로 구현할수 있습니다.
   - Swift의 initializer는 값을 반환하지 않습니다.

### 저장 프로퍼티를 위한 초기값 설정 (Setting Initial Value for Stored Property)
   - 저장 프로퍼티는 사용하기 전에 반드시 특정 값으로 초기화 돼야합니다.
   - 이 값을 기본값으로 설정할수 있고, 특정 값을 설정할수도 있습니다.
   - 값을 직접 설정하면 프로퍼티 옵저버가 호출되지 않고 값 할당이 수행됩니다.

#### 이니셜라이즈 (Initalizer)
   - 이니셜라이저는 특정 타입의 인스턴스를 생성합니다.
   - 가장 간단한 형태는 파라미터가 없고 init 키워드를 사용합니다
   - 형태는 init(){}입니다.

```swift
struct Animals {
    var name: String
    init() {
        name = "Cat"
    }
}
var Cat = Animals()
print(Cat.name)
```
#### 기본프로퍼티 (Dafault Property Value)
   - 프로퍼티 선언과 동시에 값을 할당하면 그값을 초기값으로 사용할수 있습니다.
   - 이떄까지 평소에 사용하던 방식입니다.
   - 항상 초기값을 갖는 다면 기본 프로퍼티를 사용하는것이 좋습니다.
   - 상속시 같이 상속됩니다.

### 커스터마이징 초기화 (Customizing Initialization)
   - 초기화 프로세스를 입력 값과 옵셔널프로퍼티 타입 혹은 상수 값을 할당해서 커스터마이증 할수 있습니다.

#### 초기화 파라미터(Initialization Parameter)
   - 초기화 파라미터를 정의해 사용할수 있습니다. 

```swift
struct Celsius {
    var temperatureInCelsius: Double
    init(fromFahrenheit fahrenheit: Double){
        temperatureInCelsius = (fahrenheit - 32.0) / 1.8
    }
    init(fromKelvin kelvin: Double){
        temperatureInCelsius = kelvin - 273.15
    }
}
let boilingPointOfWater = Celsius(fromFahrenheit: 212.0)
let freezingPointOfWater = Celsius(fromKelvin: 273.15)
```

#### 파라미터 이름과 인자 레이블 (Parameter Name and Arguement Label)
   - 메소드와 초기화 모두 파라미터 이름과 인자 레이블을 가지지만, 초기화파라미터는 특정메소드에서 지정하는 메소드 이름을 지정하지 않고, 초기화 식별자로 파라미터를 사용 합니다.
   - 사용자가 이 레이블을 지정하지 않으면 Swift가 자동으로 하나를 할당해 제공합니다
  \* 예시는 초기화 파라미터를 3개 입력받는 초기화와 하나만 입력받는 초기화입니다.

```swift
struct Color {
    let red, green, blue: Double
    init(red: Double, green: Double, blue: Double){
        self.red = red
        self.green = green
        self.blue = blue
    }
    init(white: Double){
        red = white
        green = white
        blue = white
    }
    let baseColor = Color(red: 1, green: 1, blue: 1)
    let whiteColor = Color(white: 1)
    let baseColor = Color(1,1,1)// 인자가 없기 떄문에 에러가 발생합니다.
}
```

#### 인자 레이블이 없는 이니셜라이저 파라미터 (Initializer Parameter Without Argument Label)
   - "_" 기호를 사용해서 인자 레이블을 생략할수 있습니다.

```swift
struct Color {
    let red, green, blue: Double
    init(_ red: Double, _ green: Double, _ blue: Double){
        self.red = red
        self.green = green
        self.blue = blue
    }
    init(white: Double){
        red = white
        green = white
        blue = white
    }
}

let baseColor = Color(1,1,1)

```

#### 옵셔널 프로퍼티 타입 (Optional Property Type)
   - 옵셔널을 사용해서 최초에 값이 없고 나중에 추가할수 있도록 만듭니다. 옵셔널 특징상 자동으로 값이없으면 nil로 초기화됩니다.

```swift
class SurveyQuestion {
    var text: String
    var response: String?
    init(text: String) {
        self.text = text
    }
    func ask() {
        print(text)
    }
}

let cheeseQuestion = SurveyQuestion(text: "Do you like cheese?")
cheeseQuestion.ask()
```

#### 초기화 중에 상수 프로퍼티 할당 (Assigning Constant Property During Initializtion)
   - 초기화는 상수 프로퍼티에 값을 할당하는 것이 가능합니다.
   - 단, 그 클래스에서만 가능하고 서브클래스에서는 변경이 안됩니다.
   - 결국, 상수는 처음에 초기화 되면 그 값으면 변경되지 않는 프로터피인게 됩니다.

```swift
class SurveyQuestion {
    let text: String
    var response: String?
    init(text: String) {
        self.text = text
    }
    func ask() {
        print(text)
    }
    func answer(){
        print(response)
    }
}

let cheeseQuestion = SurveyQuestion(text: "Do you like cheese?")
cheeseQuestion.ask()
cheeseQuestion.response = "Yes"
cheeseQuestion.answer()
```

### 기본 이니셜라이저 (Default Initializer)
   - 모든 프로퍼티의 초기값이 설정돼 있고, 하나의 초기자도 정하지 않았다면 Swift는 모든 프로퍼티를 기본값으로 초기화 하는 기본 초기자를 제공합니다.

```swift
class Animals {
    var name: String?
    var numberOfLegs = 1
    var Live = true
}
var cat = Animals()
cat.name = "cat"
cat.numberOfLegs = 4

print(cat.name)
print(cat.numberOfLegs)
print(cat.Live)
```

#### 구조체 타입을 위한 멤버쪽 이니셜라이저 (Memberwise Initializer for Structure Type)
   - 맴버쪽 이니셜라이저는 프로퍼티가 기본 값이 없어도 커스텀 이니셜라이저를 정의하지 않았다면 멤버쪽 이니셜라이저를 제공해 줍니다.
   - 이 초기자는 선언한 모든 프로퍼티를 인자로 사용합니다.

```swift
struct NoteBook{
    var width = 0.0, height = 0.0, price = 1000
}

let monnaNoteBook = NoteBook(width: 30, height: 20, price: 500)
print(monnaNoteBook)
```

### 값 타입을 위한 이니셜라이저 위임 (Initializer Delegation for Value Type)
   - 이니셜라이저에서 다른 이니셜라이저를 호출할수 있습니다.(이니셜나리저 위임)
   - 값 타입은 자기자신의 다른 이니셜라이저에서만 사용할수있습니다. (상속불가)
   - clsss타입은 superclass의 이니셜라이저를 subclass에서 호출 가능합니다 (상속가능)
   - 커스텀 이니셜라이저 선언시 기본 이니셜라이저 혹은 멤버쪽 이니셜라이저를 사용할수 없습니다. 
   - 2번째 init을 3번째 init에서 불려와 사용하는 예시입니다.

```swift
struct Size {
    var width = 0.0, height = 0.0
}
struct Point {
    var x = 0.0, y = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()
    init() {}
    init(origin: Point, size: Size){
        self.origin = origin
        self.size = size
    }
    init(center: Point, size: Size){
        let originX = center.x - (size.width / 2 )
        let originY = center.x - (size.height / 2 )
        self.init(origin: Point(x: originX,y: originY), size: size)
    }
    
}
print(Rect.init())
print(Rect.init(origin: Point(x: 4, y: 4), size: Size(width: 4, height: 4)))
print(Rect.init(center: Point(x: 4, y: 4), size: Size(width: 4, height: 4)))
```

### 클래스 상속과 초기화 (Class Inheritance and Initialization)
   - 모든 클래스의 저장 프로퍼티와 상속받은 프로퍼티는 초기화 단계에서 반드시 초기값이 할당되어야 합니다.

#### 지정 초기자와 편리한 초기자 (Desiginated Initializer and Convenience Initializer)
   - 지정 초기자는 클래스의 주(Primary) 초기자 입니다.
   - 지정 초기자는 클래스의 모든 프로퍼티를 초기화 합니다.
   - 반드시 클래스당 한개 이상의 지정 초기자가 있어야합니다.

#### 지정 초기자와 편리한 초기자의 문법 (Syntax for Designated and Convenience Initlalizer)
   - 지정초기자의 문법은 값 타입 초기자와 동일합니다
   - init(parameters){statements} 입니다.
   - 단, 편리한 초기자는 문법이 같지만 convenience init(parameters){statements} 입니다.

#### 클래스 타입을 위한 이니셜라이저 위임(Initializer Delegation for Class Type)
   - 3가지 규칙을 따릅니다
   1. 반드시 직계 superclass의 지정 초기자를 호출해야합니다.
   2. 편리한 초기자는 반드시 같은 클래스의 다른 초기자를 호출해야합니다.
   3. 편리한 초기자는 궁극적으로 지정초기자를 호출해야합니다.

![cat](assets/img/posts/Swift/ClassDelegation.jpeg)