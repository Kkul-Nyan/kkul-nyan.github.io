---
layout: post
read_time: true
show_date: true
title:  Swift Class and Structure
date:   2022-12-31
description: about Class and Structure
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
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
    //내용
}

struct StructName {
    //내용
}
```

### 클래스와 구조체 인스턴스(Class and Struct Instance)
   -