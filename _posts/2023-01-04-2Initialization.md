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
