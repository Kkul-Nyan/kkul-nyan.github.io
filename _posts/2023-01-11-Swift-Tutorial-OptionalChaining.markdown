---
layout: post
title:  Swift Optional
date:   2023-01-11
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Optional
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 
### 옵셔널 (Optional)
   - 옵셔널을 래핑하는 옵셔널체이닝 하기전에 간단히 정리할려고합니다.
   - 옵셔널의 형식은 타입선언부 뒤에 ? 문자를 씁니다. 예시 var animal: String?, let index: Int?
   - 옵셔널은 가장 어려우면서도 중요한 개념이라고 합니다. 함수형언어에서도 많이 사용합니다.
   - JAVA8의 Optional 클래스, Kotlin을 Nullable타입과 비슷하다고 합니다.
   - 값을 저장 하거나 값이 없을수도 있다는 점이 가장 큰 특징입니다.
   - 값을 반환할 때, 오류가 발생할 가능성이 있는 값은 옵셔널타입이라는 객체로 감싸서 반환합니다.
   - 맨 위의 예시처럼 int값을 string처럼 작성하면, 에러가 아닌 Optional(100)으로 반환합니다.
   - 두번째 예시를 작성하면 정수 값을 반환할수 없지만 에러가 아닌 nil을 반환합니다.
   - 옵셔널은 변수나 상수에 아무런 값이 할당되지 않는 상황을 안전하게 처리 하기 위한 방법을 제공해줍니다
   - 값의 뒤에 "!"를 통해 강제 언래핑해서 값에 접근 할 수 있습니다.
   - if문을 보시면 띄어쓰기의 중요성이 보입니다. 둘 다 틀린 형식은 아닙니다. 그러나 밑의 if문 같은경우 index! = nil 인지 index != nil인지 구분에서 문제가 생기게 됩니다.


```swift
print(Int("123"))
print(Int("Cat"))

var animal: String?
var index: Int?
index = 10
print(index) // Optional(10)
print(index!) // 10

if aniaml != nil{ print(animal!) }
if index!=nil{ print(index!)}

```
### 옵셔널 바인딩 (Optional Binding)
   - 강제 언래핑하는 다른 방법으로 옵셔널 바인딩이 있습니다. 
   - 옵셔널에 할당된 값을 임시변수나 상수에 할당해서 사용하는 것입니다.
   - ","를 통해 여러개 변수를 한번에 옵셔널로 사용할수도 있고, 한번에 언래핑 할수도 있습니다.
```swift
var a: Int?
a = 10
if var a2 = a { print(a2)}
else {print("a2 is nil")}

var pet3,pet4: String?
var pet1: String?
var pet2: String?
pet1 = "cat"
pet2 = "dog"
pet3 = "raven"
pet4 = "hamster"

if let firstPet = pet1, let secondPet = pet2, let thirdPet = pet3, let fourPet = pet4{
    print(firstPet, secondPet, thirdPet, fourPet)
}
else{
    print("nil")
}
```

### 옵셔널 체이닝 (Optional Chaining)
   - Optional Chaining은 nil일 수도 있는 프로퍼티나 메소드, 서브스크립트에 질의(qurry)를 하는 과정을 말합니다.
   - 간단히 말해 프로퍼티나 메소드 서브스크립트는 값을 갖고 있을수도 있고, 없을수도있습니다. 이때 값이 있다면 그값을 없을경우 nil을 반환합니다.
   - 여러 질의를 연결해서 할 경우, 연결된 질의에서 어느 하나라도 nil이면 전체 결과는 nil 입니다.

#### 강제 언래핑의 대체로써의 옵셔널체이닝 (Optional Chaining as Alternative to Forced Unwrapping)
   - Optional Chaining은 Optional값뒤에 "?"를 붙여서 표현 가능합니다.
   - 프로퍼티, 메소드, 서브스크립트에 Optional을 사용할수 있습니다.
   - 래핑되어있는 Optional의 값을 사용하기 위해 언래핑이라는 과정이 필요합니다.
   - 간단히 Optional을 언레핑하기 위해 "!"를 붙이는 강제언래핑 방법이 있습니다.
   - 강제언래핑의 경우 강제로 언래핑을 했는데 만약 그 그값이 없다면 런타임 에러가 발생합니다.
   - 옵셔널체이닝의 경우 언래핑을 했는데 만약 그값이 없다면 nil이 반환됩니다.
   - 옵셔널체이닝에 의해 nil 값이 호출 될수 있기 때문에 옵셔널체이닝의 값은 항상 옵셔널 값이 됩니다.
   - 옵셔널값을 반환하지 않는 프로퍼티, 메소드, 서브스크립트를 호출하더라도 옵셔널체이닝에 의해 옵셔널 값이 반환됩니다.
   - 이 옵셔널 리턴값을 이용해 옵셔널 체이닝이 성공적으로 실행 됐는지 아니면 nil을 반환했는지 확인할수 있습니다.
   - 옵셔널체이닝에 의해 호출되면 반환값과 같은 타입에 옵셔널이 붙어 반환됩니다. int를 반환시 int에 옵셔널인 ?가 붙어 int?가 반환됩니다.

``` swift
class Animal{
    var basic: Basic?
}

class Basic{
    var name: String
    init(name: String) {
        self.name = name
    }
}

let cat = Animal()
print(cat.basic!.name) //런타임 오류 nil이기때문에

let catName = cat.basic?.name
print(catName)