---
layout: post
read_time: true
show_date: true
title:  Swift Dictionary
date:   2022-12-28
description: about Dictionary collection
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
sitemap:
  changefreq: daily
  priority : 1.0
---

---
## Swift Collection Dictionary
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 기반으로 요약 및 정리 한 내용입니다. 

### Dictionary
   - Dictionary는 Key값과 Value 1쌍으로 이루어진 구성입니다. 처음에 배울때 정말 어려웠던 내용이었는데, 정말 Unity에서도 많이 사용되어서 오열했습니다. Json파일 형식으로 내보낸다거나, 게임내 단축키변경을 만드는 가장 취운방법이 Dictionary를 이용해서 Key,Value값으로 묶여주는방법이었습니다. 이걸 잘 이해를 잘 못해서 정말 고된 나날이었습니다.

#### 축약형 Dictionary
   - [Key: Value]형태로 Dictionary를 선언해 사용할 수 있습니다.

#### Dictionary 생성 및 할당
   - 타입 Dictionary이름 = \[Key데이터타입: Value데이터타입]()으로 생성 할수 있습니다. 
   - Dictionary이름[Key] = Value 로 값을 할당할수 있으며, Key값을 이용해서 Value값을 찾을수 있습니다. Value값은 Optional되어있으니 언래핑이 필요하겠네요.

```swift
var NewDictionary = [String: String]() 
NewDictionary["first"] = "Cat"
print(NewDictionary["first"])
```

#### 리터럴을 이용한 Dictionary 생성, 할당
   - Dictionay를 생성하면서 리터럴을 이용해서 여러 Key: Value값을 할당 해줄수 있습니다.

```swift
var NewDictionaray02: [Int: String] = [1: "Cat", 2: "Dog", 3:"Bird"]
var NewDictionaray02: [Int: String] = [1: "Cat", 2: "Dog", 3:"Bird"]
print(NewDictionaray02[1], NewDictionaray02[2], NewDictionaray02[3])
```

#### Dictionary의 접근과 변경
   - .iscount를 통해 몇개의 요소를 가지고 있는지 확인 할 수 있습니다.
   - .isEmpty를 통해 요소를 가지고있는지 비었는지 확인 할 수 있습니다.