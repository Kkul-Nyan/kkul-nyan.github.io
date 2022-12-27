---
layout: post
read_time: true
show_date: true
title:  Swift DataType
date:   2022-12-27
description: Basic DataType
img: banner/Swift_logo.png
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift 데이터 타입
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 01. 상수와 변수
* 기본적인 상수 let과 변수var가 있다
* let 혹수 var는 추정되지 않기때문에, 변수 선언시 작성 해주어야한다.
```swift
var x = 10
x = 20
let y = 1
y = 2
```
오류가 생기는 코드이다. 이를 알기위해선 아래 var와 let의 차이를 알아야한다

#### var
   - var는 프로그램에서 사용될 데이터를 저장 하기 위한 메모리 내의 명명된 공간을 제공한다
   - 변수에 할당된 값은 변경 가능, 초기화 할 수도 있다

#### let
   - let는 프로그램에서 사용될 데이터를 저장하기 휘한 메모리 내의 명명된 공간을 제공 한다는 점이 var와 비슷하다.
   - 어떤 값이 한번 할당되면 이후에 변경할 수 없다.
   - let은 코드 내에서 반본적으로 사용되는 값이 있을 경우에 유용하다.
   - 코드내에서 반복적으로 사용되는 특정 값을 매번 사용하는 것보다, 그 값을 상수에 할당한 다음 코드 내에서 참조하면 코드 읽기가 더 쉬워진다.
   - 나중에 값을 할당할수도 있다
```swift
let petName: String
var cat = true
if cat{
    petName = "kitty"
}
else {
    petName = "null"
}
```
   - 애플은 코드의 효율성과 실행 성능을 높이기 위해서 변수보다는 상수를 사용하라고 권장한다.
### 02. 데이터타입
#### Int: 정수형 데이터타입
   - 정수(소수점이 없는 수)를 저장하는데 사용한다.
   - 8비트, 16비트, 32비트 64비트 정수를 지원한다(Int8, Int16, Int32, Int64)
   - 부호없는 정수(UInt8,UInt16,UInt32,UInt64)를 지원한다
   - 애플은 특정 크기의 데이터 타입보다 Int데이터 타입을 권장한다.
   - Int데이터 타입은 해당 코드가 실행되는 플랫폼에 맞는 정수 크기를 사용한다.
   - 32비트 부호 있는 정수데이터 타입에 대한 최솟값과 최댓값을 출력한 것이다. 이렇게 직접 코드를 통해 확인할수 있다.
   ```swift
    print("Int32 Min = \(Int32.min) Int32 Max = \(Int32.max)")
   ```
#### Double, Float: 소수(부동소수점)형 데이터타입
   - 소수점이 있는 숫자
   - Float과 Double이 존재한다
   - Float은 32비트, 6자리 정확도를 가진다
   - Double은 64비트, 15자리 정확도를 가진다
   - 선언이 없다면, 기본적으로 Double이 기본추정 된다.
   ```swift
    let pi = 3.14159
    let anotherPi = 3 + 0.14159

    print(ype(of:pi),type(of:anotherPi))
   ```
#### Bool: 참거짓 데이터타입
   - 참 또는 거짓(1 또는 0)조건을 처리할수 있는 데이터 타입이다.
   - Boolean 데이터 타입을 처리하기 위하여 두 개의 Boolean 상수 값을 사용한다.
   - 초기값은 true가 적용된다. Bool은 일반적으로 생략한다 

### 03.만자열과 문자(Strings and Characters)
#### Charactor: 문자데이터타입
   - 문자,숫자,심볼,문장부호같은 유니코드 문자 하나를 저장
   -  따로 선언을 해줘야한다.
   - 선언이 작은 따옴표(')가 아니라 큰따옴표(")라서, 따로 선언하지 않으면 아래 이야기 할 String이 초기값이 된다.
   - 아래 처럼 Charactor로 선언 해주지 않으면, String이 된다. C#처럼 작은 따옴표를 써봤자 오류가 난다.
```swift
let mause: Character
mause = "m"
print(mause)
print(type(of: mause))
```

#### String: 문자열타입
   - String은 Foundation 프레임워크의 NSString이 bridge된 타입이기 때문에 NSString의 메소드를 캐스팅없이 사용 가능하다.
   - 단어나 문장을 구성하는 일련의 문자열이다.
   - 저장, 검색, 비교, 문자열연결, 수정 등의 기능을 포함한다.
   - 단순 연산자를 통해 문자열과 문자, 문자열과 문자열을 결합 할 수 있다.
   - 문자열 보간(String Interpolation)을 사용하는 문자열과 변수, 상수, 표현식, 함수 호출의 조합으로 만들 수도 있다.
   ```swift
   var catName = "kitty"
   var age = 5
   var cat = "\(catName)의 나이는 \(age)입니다."
   
   print(cat)
   ```
   - 문자열은 큰 따옴표(")로 묶어 표한 한다.
   - 여러줄 문자열 리터럴
      - 여러줄의 문자열 즉 문단 이상을 사용하고 싶은 경우 큰 따옴표 3개(""")로 묶어서 사용할수 있다.
      - 여러줄 문자열 리터럴을 사용할 때는 첫 시작의 """의 다음줄부터 마지막 """의 직전까지를 문자열로 봅니다.
      - 여러줄 문자열을 사용하여 줄바꿈을 하고 싶다면 백슬래쉬를 사용합니다.
      - 문자열의 시작과 끝에 각각 빈줄을 넣고 싶다면 한 줄을 띄어서 문자열을 입력하면 됩니다
      - 들여쓰기의 경우, 들여쓰기 기준은 뒤에있는 """의 위치입니다.
   ```swift
   let catDream = """ 

   this cat try to move other place for kitty. \ 
   but kitty doesn't have enough time to find safty place.

   """
   ```
   - String형은 특수 문자를 사용 할 수 있습니다.
   - 문자열의 개별 문자를 for-in loop을 사용해서 접근 할 수 있습니다.
   ```swift
   for char in "Cat!"{
    print(char)
   }
   ```
   - 문자 배열을 이용해 문자열의 초기화 메소드에 인자로 넣어 문자열을 생성 할수 있다.
   ```swift
   let cat: [Character] = ["c", "a", "t"]
   let catSpelling = String(cat)
   print(catSpelling)
   ```

#### 단항, 이항, 삼항 연산자를 지원한다
```swift
let b = 10
var a = 5
a = b 
print(a)
```
