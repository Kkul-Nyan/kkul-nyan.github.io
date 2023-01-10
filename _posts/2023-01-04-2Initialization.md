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

![ClassDelegation](assets/img/posts/Swift/ClassDelegation.png)

#### 2단계 초기화 (Two-Phase Initialization)
   - 클래스 초기화는 2단계로 진행됩니다.
   1. 각 저장된 프로퍼티는 초기값으로 초기화 됩니다. 모든 저장된 프로퍼티의 상태가 결정되면 2단계가 시작됩니다.
   2. 저장된 프로퍼티를 커스터마이징 하는 단계입니다. 이후 새로운 인스턴스의 사용이 준비되었다고 알려주게됩니다.

#### 안전확인 (Safety-check)
   - Swift 컴파일러는 2단계초기화가 에러없이 끝나는 것을 보장하기 위해 4단계 안전확인을 합니다.
   1. 지정 초기자는 클래스 안에서 초기화를 superclass의 초기자에게 위임하기 전에 모든 프로퍼티를 초기화 해야합니다.
   2. 지정 초기자는 반드시 상속된 값을 할당하기 전에 superclass의 초기자로 위임을 넘겨야 합니다.
   3. 편리한 초기자는 반드시 어떤프로퍼티를 할당하기 전에 다른 초기자로 위임을 넘거야합니다.
   4. 초기화의 1단계가 끝나기 전에는 self의 값을 촘조하거나 어떤 프로퍼티, 메소드 등을 호출하거나 읽을수 없습니다.

#### 이니셜라이저의 상속과 오버라이딩 (Initializer Inheritance and Overriding)
   - Swift에서는 기본적으로 subclass에서 superclass의 이니셜라이저를 상속하지 않습니다.
   - 클래스에서 모든 프로퍼티의 초기 값이 지정돼 있고 아무런 커스텀 초기자를 선언하지 않았다면 기본초기자 init()을 사용할수 있습니다.
   - subclass에서 상속자를 오버라이드하기 위해선 그 초기자에 override 키워드를 붙이고 재정의 해야합니다.

```Swift
class Vehicle {
    var nuberofWheels = 0
    var description: String {
        return "\(nuberofWheels) wheel(s)"
    }
}

class Car: Vehicle {
    override init() {
        super.init()
        nuberofWheels = 4
    }
}
var car = Car()
print(car.description)
```

#### 자동 초기자 인스턴스 (Automatic Initializer Inheritance)
   - subclass는 superclass의 초기자를 기본적으로 상속하지 않습니다. 하지만 특정 상황에서 자동으로 상속 받습니다.
   1. subclass가 지정초기자를 정의하지 않으면 자동으로 모든 지정초기자를 상속합니다.(편리한초기자 포함)
   2. subclass가 superclass의 지정초기자를 모든 구현한 경우 자동으로 수퍼클래스의 편리한 초기자를 추가합니다.

#### 지정초기자와 편리한 초기자의 사용
   - 바로 아래 예시는 unname에서 초기값을 지정하지 않았지만, 편리한 초기자에 의하 "Unname"을 갖게 되었습니다.

```Swift
class Animal {
    var name: String
    var description: String {
        return "name is \(name)"
    }
    init(name: String) {
        self.name = name
    }
    convenience init() {
        self.init(name: "Unnamed")
    }
}

let Cat = Animal(name: "Cat")
print(Cat.description)
let unname = Animal()
print(unname.description)
```
   - 아래 예시는 Animal을 상속받는 새로운 클래스입니다.
   - superclass의 init(name:)을 상속 받아 지정초기자로 생성된 init(name: , isWings:)입니다
   - 그 지정초기자를 편리한 초기자 conveninence init(name: String)에서 오버라이딩해서 사용합니다.
   - 지정초기자에 override키워드가 붙은게 아니지만, 분명히 상속받아 생성된 지정초기자입니다.

```Swift
class Bird: Animal {
    var isWings: Bool
    override var description: String {
        return "name is \(name) and iswings is \(isWings)"
    }
    init(name: String, isWings: Bool) {
        self.isWings = isWings
        super.init(name: name)
    }
    override convenience init(name: String) {
        self.init(name: name, isWings: true)
    }
    convenience init() {
        self.init(name: "UnnamedBird", isWings: true)
    }
}

let Raven = Bird(name: "Raven")
let Parrot = Bird(name: "Parrot" , isWings: true)
let Unname2 = Bird()
print(Raven.description)
print(Parrot.description)
print(Unname2.description)
```
   - 아래 예시는 Bird를 상속받는 새로운 클래스입니다.
   - isPet 프로퍼티의 경우, 값이 지정되어있으므로, subclass는 superclass의 초기자를 모두 자동으로 상속받습니다.
   - 따라서, 3가지 초기자를 사용할수 있습니다.

```Swift
class PetBird: Bird{
    var isPet = true
    var petDesription: String{
        var output = "\(name) is Egg or not? \(isEgg) and is Pet?"
        output += isPet ? "Yes" : "No"
        return output
    }
}
let newRaven = PetBird(name: "NewRaven", isEgg: true)
let newParrot = PetBird(name: "NewParrot")
let newUnnamed = PetBird()
print(newRaven.petDesription)
print(newParrot.petDesription)
print(newUnnamed.petDesription)

var newBirds = [PetBird(), PetBird(name: "Cute"),PetBird(name: "Black", isEgg: true)]
newBirds[0].name = "White"
newBirds[0].isPet = false

for pet in newBirds {
    print(pet.petDesription)
}
```

### 실패 가능한 초기자 (Failable Initializer)
   - 초기화 과정 중에 실패할 가능성이 있다면 init뒤에 "?"를 사용해 실패가 가능한 초기자라고 표시 할 수 있습니다.
   - 실패 가능한 초기자는 반환값으로 옵셔널 값을 생성합니다.
   - 따라서, 실패하는 부분에서 nil을 반환하는 코드를 작성해 초기화가 실패했다는것을 나타낼수 있습니다.
   - 엄밀히 말하면 init은 값을 반환하지 않습니다. nil을 반호나하는 return nil 코드는 사용하지만, 성공한경우 return키워드를 사용하지 않습니다.

```Swift
struct Animal {
    let species: String
    init?(species: String) {
        if species.isEmpty {return nil}
        self.species = species
    }
}

let White = Animal(species: "")
print(White?.species) // nil값이 확인됩니다.
let Black = Animal(species: "Cat")
//print(Black.species) - 이렇게 작성시 오류가 발생합니다.
print(Black?.species) //- Optional로 되어있습니다.
```