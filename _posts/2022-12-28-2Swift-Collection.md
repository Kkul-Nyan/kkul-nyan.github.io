---
layout: post
read_time: true
show_date: true
title:  Swift Collection
date:   2022-12-28
description: about Collection
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift Collection
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 


![image](assets/img/posts/Collection/Collection.png)
\* 정말 좋은 이미지 자료입니다. C# 공부떄는 단순히 형식만 외운다보니 헷갈릴 때가 많았는데, 이 이미지 이후 그부분이 싹 사라졌습니다.

### 배열의 종류
   - Swift는 Array, Set, Dictionary 배열을 지원합니다.
   - 배열을 var에 할당하면, 배열은 변경이 가능하지만, let에 할당하면 변경이 안됩니다.

### Array
#### 배열의 축약형문법
   - 배열타입은 Array, 축약형으로 [Element]형태로 사용할수 있습니다.
   - 배열의 선언은 [배열의타입 이름 = [데이터타입]() 으로 선언해 둘수있습니다
   - append로 추가할수 있습니다.
   - []를 통해 Array를 비워 줄 수 있습니다.

```swift
var Cats = [Int]()
print(Cats)
Cats.append(3)
print(Cats)
Cats = []
print(Cats)
```

 #### 기본 값으로 빈배열 생성
   - repeating 메소드와 count 메소드를 이용해 기본 값으로 빈 배열을 생성할수 있습니다.

```swift
var fourCats = Array(repeating: 0.0, count: 4)
print(fourCats)
var BigCats = [Int]()
BigCats = Array(repeating: 1, count: 5)
print(BigCats)
```

#### 다른 배열을 추가한 배열의 생성
   - \+ 연산자를 통해 배열들을 합칠 수 있습니다.
   - 단, 같은 데이터타입의 배열끼리만 합칠수 있습니다.(예시 : int배열 + int배열)

```swift
var NewIntArray = fourCats + BigCats
print(NewIntArray)
//먼저 BigCats를 Double형으로 만들어주어야합니다. 
```

#### 리터럴을 이용한 배열의 생성
   - [value1, value2, value3] 형태를 이용해 배열을 생성 할수 있습니다.
   - 저는 처음에 이방법으로 생성시 Cannot convert value of type '[String]' to specified type 'String' 오류가 생겨 당황했습니다
   - String 역시 []사이에 넣어줘야했는데, []없이 String만 선언했다는 의미입니다.


```swift
var catsName: [String] =["KKUL","NYNONG","MiLLION"]
print(catsNAme)
``` 
