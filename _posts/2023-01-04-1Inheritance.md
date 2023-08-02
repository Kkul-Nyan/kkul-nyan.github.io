---
layout: post
title:  Swift Inheritance01
date:   2022-12-31
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Inheritance01
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 상속 정의 (Inheritance)
   - 클래스는 메소드, 프로퍼티와 다른 특징을 다른클래스로부터 상속 받아 올수 있습니다.
   - 저장된 프로퍼티와 계산된프로퍼티와 상관없이 상복받은 프로퍼티에 프로퍼티 옵저버를 설정해서 반응할수 있습니다.

### 기반 클래스 정의 (Defingin a Base Class)
   - 다른 어떤 클래스로부터도 상속받지 않은 클래스입니다.
   - 상속을 해주는 클래스입니다.
   - SuperClass라고도 합니다.

```swift
class Animals {
    var name = "base"
    var numberofLeg = 0
    var description: String{
        return "\(name) has \(numberofLeg) legs"
    }
    func captureAnimal(){
        
    }
}
let someAnimal = Animals()
print("Animal \(someAnimal.description)")
```

### 서브클래스 (Subclassing)
   - 상속 받는 클래스입니다.
   - 부모로 부터 상속받고 자기 자신 고유의 특성도 추가할수 있습니다.
   - 서브클래스의 선언은 class SubClassName: SomeSuperClass 입니다

```swift
let someAnimal = Animals()
print("Animal \(someAnimal.description)")

class Dogs: Animals {
    var bark = true
}
let dog = Dogs()
dog.name = "dog"
dog.numberofLeg = 4
print(dog.description)
```

#### 오버라이딩 (Overriding)
   - 서브클래스는 부모클래스에서 상복받은것을 재정의하는 것을 오버라이딩이라 합니다.
   - 메소드, 타입메소드, 인스턴스 프로퍼티, 타입 프로퍼티, 서브스크립트 모두 가능합니다
   - 오버라이드는 다른 선언앞에 override 키워드를 붙여줘야합니다.

#### Super
   - super키워드와 점문법 혹은 인덱스 구문으로 부모 클래스의 메소드, 프로퍼티, 서브스크립트에 접근할수 있습니다.

#### 메소드 오버라이드 (Overriding Method)
   - 상속받은 메소드를 오버라이드 하기위해 메소드 선언 앞에 override 키워드를 붙여주면됩니다.

```swift
class Cats: Animals {
    override func captureAnimal() {
        print("YES")
    }
}
let cat = Cats()
cat.captureAnimal()
```

#### 프로퍼티 오버라이드 (Overriding Property)
   - 저장된 프로퍼티, 계산된프로퍼티 모두 오버라이드 가능합니다.
   - 오버라이드시에는 프로퍼티의 이름과 타입을 명시해야합니다.
   - 상복받은 읽기전용 프로퍼티도 getter/setter를 정의해서 읽기/쓰기가 가능한 프로퍼티로 변경해서 사용 가능합니다.
   - 반대로 읽고//쓰기가 가능한 프로퍼티를 읽기전용으로 선언하는것은 할수 없습니다.

```swift
class Cats: Animals {
    var AnimalType = 1
    override var description: String {
        return "Animaltyep : \(AnimalType)" + super.description
    }
    override func captureAnimal() {
        print("YES")
    }
}
let cat = Cats()
cat.captureAnimal()
print(cat.description)
```

#### 프로퍼티 옵저버 오버라이드 (Overriding Property Observer)
   - 이미 부모클래스에 선언된 프로퍼티 옵저버도 서브클래스에서 재정의해 사용할수 있습니다.
   - 단, 상수 프로퍼티와 읽기전용 프로퍼티에는 옵저버를 붙일 수 없습니다.(값의 변동이 없음)

### 오버라이드 방지 (Preventing Override)
   - 오버라이드 되는 것을 방지할려고 final 키워드를 사용합니다.
   - final 키워드로 선언되면 override 되는것을 막을수 있습니다.
   - 클래스 전체를 final 선언 할수도 있습니다.