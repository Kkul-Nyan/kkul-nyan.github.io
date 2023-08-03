---
layout: post
title:  Swift Tuple
date:   2022-12-31
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Tuple
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### Tuple
   - 튜플은 스위프트 프로그래밍 언어에서 가장 강력한 기능중 하나입니다.
   - 여러값을 하나의 개체에 일시적으로 묶는 방법입니다.
   - 튜플에 저장되는 항목들은 어떠한 타입도 상관없으며, 저장된 값들이 모두 동일한 타입이어야한다는 제약도 없습니다.
   - 튜플의 요소들은 여러 다른 방법들을 사용해서 접근할수 있습니다.
   - 특정 튜플 값은 인덱스로 위치를 참조하면 간단하게 접근 할수 있습니다.( 마치 Array처럼 접근)

```swift
let anything = (10,11,2,4.3,"Cat")
var Animal = anything.4

print(Animal)
print(anything.4)
```

#### 모든 값을 추출하여 변수 또는 또는 상수에 할당 가능

```swift
let (num1,num2,num3,num4,animal) = anything
print(num1,num2,num3,num4,animal)
```

#### 선택적으로 추출 할수도 있고, 특정값을 무시하고 추출도 가능
   - 무시하고 추출하고 싶을시 "_"을 사용해서 특정 항목만 무시 가능합니다

```swift
let (num1,num2,_,num3,_) = anything
print(num1,num2,num3)
```

#### 튜플에 저장된 값에 할당된 이름은 각 값을 참조하는데 사용

```swift
let cat = (age: 10, length: 25.5, name: "Kkul")
print(cat.age)
print(type(of: cat))
```