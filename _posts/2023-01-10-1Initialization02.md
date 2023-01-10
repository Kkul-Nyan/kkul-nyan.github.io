---
layout: post
read_time: true
show_date: true
title:  Swift Inheritance02
date:   2023-01-10
description: about Inheritance02
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift Inheritance02
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

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
   - 실패 가능한 초기자를 실패가 가능하지 않은 초기자에 위임해서 특정 상황에만 실패하는 초기자로 만들수 있습니다

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

#### 열거형에서 사용하는 실패 가능한 초기자 (Failable Initializer for Enumeration)
   - 열거형에서도 실패 가능한 초기자를 사용할수 있습니다.
   - 지정된 값이 아니면 당연히 default값이 되면서 nil이 반환됩니다.

```swift
enum KeySetting {
    case attack,defense
    init?(key: Character){
        switch key {
        case "A":
            self = .attack
        case "B":
            self = .defense
        default:
            return nil
        }
    }
}

let attackButton = KeySetting(key: "A")
if attackButton != nil {
    print("Success Attack")
}
else {
    print("fail Attaack")
}

let defenseButton = KeySetting(key: "D")
if defenseButton != nil {
    print("Success Defense")
}
else{
    print("fail Defense")
}
```

#### 열거형에서 Raw값을 사용하는 실패 가능한 초기자 (Failable Initializer for Enumeration with Raw Value)
   - 각 케이스에 지정되어있는 Raw값을 초기자 인지로 넣어 초기화에 사용할수 있습니다.
   - 앞의 경우보다 초기자 구현이 훨씬 간단해졌습니다.

```swift
enum KeySetting: Character {
    case attack = "A", defense = "B"
}

let attackButton = KeySetting(rawValue: "A")
if attackButton != nil {
    print("Success Attack")
}
else {
    print("fail Attaack")
}

let defenseButton = KeySetting(rawValue: "D")
if defenseButton != nil {
    print("Success Defense")
}
else{
    print("fail Defense")
}
```

#### 초기자 실패의 생성 (Propagation of Initializer Failure)
   - 실패가능한 초기자에서 실패가 발생하면 즉시 관련된 초기자가 중단 됩니다.
   - 첫번째와 2번째 인자는 각각, species와 age가 조건에 맞지 않아 초기자가 중단됩니다
   - 따라서 desciption을 하여도 인자가 nil이기때문에 description 역시 nil이 됩니다. 
   
```swift
class Animal {
    let species: String
    init?(species: String){
        if species.isEmpty {return nil}
        self.species = species
    }
}
class DetailAnimal: Animal {
    var age: Int
    init?(species: String, age: Int){
        if age < 1 {return nil}
        self.age = age
        super.init(species: species)
    }
    var desciption: String{
        return "it is \(species) and age is \(age)"
    }
}
var FindAnimal = [DetailAnimal(species: "", age: 5),DetailAnimal(species: "Dog", age: 0), DetailAnimal(species: "Cat", age: 3)]
for animal in FindAnimal {
    print(animal?.desciption)
}
```

#### 실패 가능한 초기자의 오버라이딩 (Overriding Failable Initializer)
    - superclass의 실패가능한 초기자를 subclass에서 실패불가능한 초기자로 오버라이딩 할 수 있습니다.
    - 단, 그 반대는 불가능합니다
    - 