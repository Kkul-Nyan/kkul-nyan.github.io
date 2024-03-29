---
layout: post
title:  Swift Property
date:   2022-12-31
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Property
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 프로퍼티(Property)
   - 클래스, 구조체, 열거형과 관련된 값입니다.
   - 저장 프로퍼티와 계산된 프로퍼티가 있습니다.
   - 저장 프로퍼티는 말그대로 값을 저장하고 있는 프로퍼티입니다.
   - 계산된 프로퍼티는 값을 저장하지 않고 특정하게 계산한 값을 반환해 주는 프로퍼티입니다.
   - 계산된 프로퍼티는 모두에서 사용가능하지만, 저장프로퍼티는 클래스와 구조체에서만 사용 가능합니다.

### 저장 프로퍼티(Stored Property)
   - 단순히 값을 저장하고 있는 프로퍼티입니다.
   - let 이나 var 키워드를 이용해서 선언해 사용할수 있습니다.

#### 상수구조체 인스턴스의 저장 프로퍼티(Stored Property of Constant Structure Instance)
   - 구조체를 상수로 선언하면 그 구조체 인스턴스의 프로퍼티를 변경할수 없습니다.
   - 클래스의 경우는 참조타입이기 때문에 let으로 상수선언해도 값 변경 가능하다.

```swift
struct StructName {
    var width = 1
    var height = 1
}
let StructInstance = StructName(width: 10, height: 10)
StructInstance.width = 100
//에러발생
//StructName(width: 5, height: 5)으로 해봤자 값복사기 때문에 의미없다. 결국 선언값인 1,1이다

class ClassName{
    var wid = 10
    var hei = 10
}
let ClassInstance = ClassName()
ClassInstance.wid = 100
print(ClassInstance.wid)
```

#### 지연 저장 프로퍼티(Lazy Stored Property)
   - 지연 저장 프로퍼티는 값이 처음으로 사용 되기 전에는 계싼되지 않는 프로퍼티입니다.
   - 프로퍼티 앞에 lazy를 선언하면 됩니다.
   - 반드시 변수는 var로 선언되어야합니다( lazy var)
   - 특정 요소에 의존적이어서 그 요소가 끝나기 전에 적절한 값을 알지 못하는 경우에 유용합니다.
   - 자동클로저의 프로퍼티 버전같은 느낌과 비슷합니다.
   - 고로, 복잡한 계산이나 부하기 많이 걸리는 작업에 이용하면 실제 사용되기 전까지는 실행되지 않아서 부하나 복잡한 계산을 피할수 있습니다.
   - 전역변수로 선언시 오류가 생깁니다. 지역변수에서 사용해주어야합니다.

```swift
class DataSave{
    var Animal = ["Dog", "Cat"]
}

class Date{
    lazy var datas = DataSave()
}

print(DataSave().Animal)
let manage = Date()
manage.datas.Animal.append("Bird")
print(DataSave().Animal) //Bird가 추가되지않았습니다.
print(manage.datas.Animal) //Bird가 추가되어있습니다.
```

#### 저장 프로퍼티와 인스턴스 변수(Stord Property and Instance Variable)
   - Swift는 프로퍼티의 이름,타입,메모리 관리등의 모든 정보를 프로퍼티를 선언하는 한곳에 정의하게 됩니다.

### 계산된 프로퍼티(Computed Property)
   - 클래스, 구조체, 열거형은 계산된 프로퍼티를 사용할수 있습니다.
   - 실제값을 저장하는 것이 아니라 getter와 setter를 제공해 값을 탐색하고 간접적으로 다른 프로퍼티 값을 설정할수 있습니다.
   - C#에서도 getter, setter를 데이터 접근보호를 공부하면서 배우면서도 힘들었던 부분이었던게 기억납니다.
   - C#을 공부할때는 읽기, 쓰기 로 이해가 잘안되서 단순히 외워보기까지했습니다.
   - Rect는 딱히 어떤값을 가지고있지는 않습니다. 단지 Get과 Set을 통해 가지고 있는 연산식을 통해 프로퍼티를 구할뿐입니다.
   - square을 선언할때 받은 값으로 Get함수에서 centerX,centerY가 (5,5)라 연산하고, 사이즈가10*10를 받아왔을뿐입니다.
   - square.center를 통해 Set함수를 통해 newCenterX,newCenterYrㅏ(10,10)에 받아온 Get에서 가진 사이즈가 10*10으로 기억하고 연산할뿐입니다.

```swift
struct Point {
    var x = 0.0, y = 0.0
}
struct Size {
    var width = 0.0, height = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()
    var center: Point{
        get{
            let centerX = origin.x + (size.width/2)
            let centerY = origin.y + (size.height/2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter){
            origin.x = newCenter.x - (size.width/2)
            origin.y = newCenter.y - (size.height/2)
        }
    }
}

var square = Rect(origin: Point(x: 0.0,y: 0.0),
                  size: Size(width: 10.0,height: 10.0))
let initialSquareCenter = square.center
square.center = Point(x: 15.0,y: 15.0)
print("Square.origin is now at (\(square.origin.x), \(square.origin.y))")
```

#### Setter 선언의 간략한 표현 (Shorthand Setter Declaration)
   - set(newCenter)라고 명시하지않고, (newCenter)를 적어주지 않아도 newValue로 사용가능합니다.

#### 읽기 전용 계산된 프로퍼티 (Read-Only Computed Property)
   - getter만 있고 setter를 제공하지 않으면 읽기전용 계산된 프로퍼티라고 합니다.
   - 반드시 반환값을 제공하지만 다른값을 지정할수 없는 프로퍼티입니다.
   - getter로 값을 읽어 내부에 맞게 연산만해주는 것 뿐입니다.

### 프로퍼티 옵저버(Property Observe)
   - 새 값이 설정(set) 될 때마다 이 이벤트를 감지 할수 있는 옵저버입니다.
   - 이벤트가 발생하면 감지하기에 값이 변동이 없어도 호출됩니다.
   - 지연저장 프로퍼티에서는 사용할수 없습니다. 
   - 서브클래스의 프로퍼티에 옵저버를 정의하는 것도 가능합니다.
   - setter에서 값의 변화를 감지 할수 있기 때문에 따로 옵저버를 정의할 필요는 없습니다.
   - 2가지 옵저버를 제공합니다.
   1. willSet : 값이 저장되기 바로 직전에 호출됨
   2. didSet : 새값이 저장되고 난 직후에 호출됨
   - willSet에서는 새값의 파라미터명을 지정할수 있는데, 지정하지 않으면 기본값으로 newValue를 사용합니다
   - didSet에서는 파뀌기 전의 값의 파라미터 명을 지정할수 있는데, 지정하지 않으면 기본값으로 oldValue를 사용합니다.

```swift
class StepCounter {
    var totalSteps: Int = 0 {
        willSet(newTotalSteps) {
            print("About to set totalSteps to \(newTotalSteps)")
        }
        didSet{
            if totalSteps > oldValue {
                print("Added \(totalSteps - oldValue) steps")
            }
        }
    }
}
let stepCounter = StepCounter()
stepCounter.totalSteps = 200
stepCounter.totalSteps = 300
```

### 전역변수와 지역변수(Global and Local Variable)
   - 옵저버 기능은 전역변수, 지역변수 모두에서 이용 가능합니다.
   - 전역변수란 함수, 메소드, 클로저 혹은 타입 컨텍스트 밖에 정의된 변수입니다.
   - 지역변수는 그안에 선언된 변수를 말합니다(특정 Func에서 선언된 변수 등등)
   - 전역 상수와 변수는 지연저장 프로퍼티와 같이 지연계산 됩니다. 따라서 lazy 선언해줄 필요는 없습니다.

### 타입프로퍼티(Type Property)
   - 인스턴스 프로퍼티는 특정 인스턴스에 속한 프로퍼티를 말합니다.
   - 새로운 인스턴스가 생성될 때마다 새로운 프로퍼티도 같이 생성됩니다.
   - 타입 프로퍼티는 특정 타입에 속한 프로퍼티로 그타입에 해당하는 단 하나의 프로퍼티만 생성됩니다.
   - 특정 타입의 모든 인스턴스에 공통으로 사용되는 값을 정의할 때 유용합니다.
   - 인스턴스 프로퍼티와는 다르게 항상 초기값을 지정해서 사용해야합니다. 타입자체에 초기자(Initializer)가 없어 초기화 할 곳이 없습니다.

#### 타입 프로퍼티 구문(Type Property Syntax)
   - static 키워드를 사용해서 선언합니다.
   - class로 선언된 프로퍼티는 서브클래스에서 오버라이드 가능합니다.
   - class에 선언하는게 아니라 프로퍼티인만큼 내부에서 프로퍼티 선언할때 프로퍼티에 선언해주야합니다
   - 구조체, 열거형, 클래스 타입에서 사용가능합니다.
   - 타입 프로퍼티를 쓰는 이유는 다른곳에 할당해서 값이 변동해도, 타입프로퍼티는 하나이기 때문에 직접 접근하지않으면 변경되지 않기 때문에 특정 기준점등으로 사용하기 좋습니다. ex) 특정 상황의 최대값 or 최소값

```swift
struct StructureName{
    static var width
    static var height
}
```

#### 타입 프로퍼티의 접근과 설정 (Qurrying and Setting Type Property)
   -  Dot연산자로 프로퍼티의 값을 가져오고 할당 할수 있습니다.

```swift
struct StructureName{
    static var width = 10
    static var height = 10
}

StructureName.width = 100
print(StructureName.width)
```

