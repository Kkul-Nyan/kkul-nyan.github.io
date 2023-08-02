---
layout: post
title:  Swift Class and Structure
date:   2022-12-31
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Class and Structure
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 클래스와 구조체
   - 프로그램의 코드를 조직화 하기 위해 일반적으로 사용합니다
   - Swift는 다른 언어와 다르게 interface파일과 implementation 파일을 분해서 만들지 않아도 됩니다.
   - 하나의 파일에 구조체나 클래스를 정의하면, Swiftrㅏ 알아서 해당 클래스와 그조체를 사용할수 있는 인터페이스를 생성해줍니다.

### 클래스와 구조체의 비교 (Comparing Class and Structure)
#### 공통점
   1. 값을 저장하기 위해 프로퍼티 정의
   2. 기능을 제공하기 위한 메소드 정의
   3. 특정 값을 접근할수 있는 subscrpt 정의
   4. 초기 상태를 설정할수 있는 initializer 정의 : initializer는 자원을 할당함
   5. 기본 구현에서 기능 확장
   6. 프로토콜 순응(conform)
   
#### 클래스에서만 가능한 기능
   1. 상속(Inheritance)
   2. 타입캐스팅(Type Casting) : 런타임에 클래스 인스턴스의 타입을 확인
   3. 소멸자(Deinitializer) : 할당된 자원을 해체
   4. 참조 카운트(Reference counting) : 클래스 인스턴스에서 하나 이상의 참조가 가능

### 선언 문법 (Definition Syntax)
   - class, struct 키워드를 이름앞에 선언할 수 있습니다.
   - class, struct를 선언할 때마다 Swift에서는 새로운 타입을 선언하는 것입니다.

```swift
class ClassName{
    var width = 1
    var height = 1
}

struct StructName {
    var resolution = ClassName()
    var interlaced = false;
    var frameRate = 0.0
    var name: String?
}
```

### 클래스와 구조체 인스턴스(Class and Struct Instance)
   - 이름 뒤에 빈 괄호를 적으면 각각의 인스턴스를 생성할수 있습니다.

```swift
let ClassInstance = ClassName()
let StructInstance = StructName()
```

### 프로퍼티 접근(Accessing Property)
   - Dot문법을 통해 클래스/구조체 인스턴스의 프로퍼티에 접근할수 있습니다.
   - 인스턴스를 통해 접근할수도 있습니다.
   - 하위레벨 프로퍼티도 Dot문법을 통해 접근할수 있습니다.
   - Dot문법을 통해 값을 할당 할수도 있습니다.

```swift
print(ClassName().height)
print(StructName().frameRate)
print(StructInstance.interlaced)
print(StructName().resolution.height)
ClassInstance.resolution.height = 1200
print("now \(ClassInstance.resolution.height)")
```

### 구조체형 맴버 초기화 (Memberwise Initializer for Structure Type)
   - 모든 구조체는 초기화시 프로퍼티를 선언할수 있는 초기자를 자동으로 생성합니다.
   - width와 height 프로퍼티만 정의했다면 자동으로 사용 가능하다는 의미입니다.

```swift
let Xlarge = StructName(width: 1980, height: 1080)
```

### 구조체와 열거형은 값타입(Structure and Enumeration Are Value Type)
   - 구조체와 열거형은 새로운 값타입입니다.
   - 함수에서 상수나 변수에 전달될 때 그 값이 복사되서 전달 된다는 의미입니다
   - 복사되서 전달된다는것은 원본은 바뀌지 않았다는것입니다.
   - 새로운 인자에 값을 할당해주고 변경해도 새로운인자만 변경됩니다.

```swift
let Xlarge = StructName(width: 1980, height: 1080)
var newX = Xlarge
newX.height = 2500
print(newX.height)
print(Xlarge.height)
```

### 클래스는 참조타입(Class Are Reference Type)
   - 변수나 상수에 값을 할당을 하거나 함수에 인자로 전달할 때 그 값이 복사되지 않고 참조 됩니다.
   - 참조 된다는 의미는 그 값을 갖고 있는 메모리를 보고있다는 의미입니다.
   - 즉 새로운 메모리를 만든게 아니라 그 원본 메모리가 바뀌게 됩니다.
   - 구조체와 다르게, 값을 변경하면 바뀌게 됩니다.

#### 식별 연산자(Identity Operator)
   - 클래스는 참조 타입이기 때문에 여러 상수와 변수에서 같은 인스턴스를 참조 할 수 있습니다.
   - 상수와 변수가 같은 인스턴스를 참조하고 있는지 비교하기 위해 식별 연산자를 사용합니다
   - === : 두 상수나 변수가 같은 인스턴스를 참조하고 있는 경우 참
   - !== : 두 상수나 변수가 다른 인스턴스를 참조하고 있는 경우 참

#### 포인터(Pointer)
   - Swift에서 상수나 변수가 특정 타입의 인스턴스를 참조하고 있다는 것은 위 포인터와 유사합니다
   - 실제 메모리를 직접 가르키고 키워드로 표시하는것과 다르게 다른상수와 변수처럼 정의해 사용합니다.

### 클래스와 구조체의 선택(Choosing Between Class and Structure)
   - 결국 클래스와 구조체의 큰차이는 참조타입인가 값타입인가입니다.
   - 클라스는 참조되므로 값이 변경되고, 구조체는 초기값을 복사해갈뿐이기 때문에 초기값이 바뀌지않습니다.
   - 대신, 메모리에서도 차이가 날것입니다.
   - 구조체와 클래스 중 선택을 해야할때, 구조체를 사용하는것을 고려할 4가지가 있습니다.
   1. 구조체의 주목적이 관계된 간단한 값을 캡술화 하기 위한것인 경우
   2. 구조체의 인스턴스가 참조되기보다 복사되기를 기대하는 경우
   3. 구조체에 의해 저장된 프로퍼티가 참조되기보다 복사되기를 기대하는 경우
   4. 구조체가 프로터티나 메소드 등을 상속할 필요가 없는 경우
   - 위 경우를 제외한 모든 경우에는 구조체가 아니라 클래스를 사용하면 됩니다.

### String,Array,Dictionary의 할당과 복사 동작(Assignment and Copy Behavior for String, Array, and Dictionary)
   - String, Array, Dictionary 같은 기본 데이터 타입은 구조체로 구현되있습니다. 다른 의미로 변수나 상수에 할당되거나, 메소드나 함수에 인자로 넘길떄, 단순히 값이 복사되어 갈뿐입니다.
   - 반면, Foundation의 NSString,NSArray,NSDictionary는 클래스로 구현 돼 있습니다. 이 데이터들은 참조가 됩니다. 이점을 유의해야합니다. 