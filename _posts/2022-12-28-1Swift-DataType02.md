---
layout: post
title:  Swift DataType02
date:   2022-12-27
image: Swift_logo.jpg
tags: [Swift]
---

---
## Swift 데이터 타입02
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 01.유니코드
   - 유니코드는 전 세계의 모든 문자를 컴퓨터에서 일관되게 표현하고 다룰 수 있도록 설계된 국제 표준이다. 
   - Swift의 네이티브 문자열 타입은 유니코드 스칼라 값으로 만들어 졌습니다. 하나의 유니코드는 21비트의 숫자로 구성돼있다.

#### 문자세기
   - 문자열의 문자의 갯수를 세기 위해서는 count를 사용한다
   ```swift
   let cat = "cat is cat. just cat" 
   print("cat's count is \(cat.count)")
   ```
   
#### 문자열의 접근과 수정
   - 문자열의 수정과 접근은 문자열 메소드 혹은 프로퍼티를 이용하거나 서브스크립트(subscript) 문법을 이용해 할 수 있습니다.
   - 프로퍼티(property)는 일부 객체 지향 프로그래밍 언어에서 필드(데이터 멤버)와 메소드 간 기능의 중간인 클래스 멤버의 특수한 유형이다. 프로퍼티의 읽기와 쓰기는 일반적으로 게터(getter)와 세터(setter) 메소드 호출로 변환된다.
   - 서브스크립트란 클래스, 구조체 그리고 열거형에서 스크립트를 정의해 사용할 수 있습니다. 서브스크립트란 콜렉션, 리스트, 시퀀스 등 집합의 특정 멤버 엘리먼트에 간단하게 접근할 수 있는 문법입니다. 

#### 문자열 인덱스
   - startIndex = 맨 앞 문자
   - endIndex = 맨 뒤 문자
   - index(before:) = before기준의 앞 문자
   - index(after:) = after 기준의 뒤 문자
   - index(_:offsetBy:) = 앞에 기준을 정하고 그 기준으로부터 몇번째 문자열을 지정한 문자
   - 로 문자열에 특장 문자에 접근 할수 있다
   - 인덱스를 벗어나는 문자를 가져오려고하면 nil이 아니라 오류가 뜬다
   - 문자열의 개별 문자를 접근하기 위해서는  indices(index의 복수형) 프로터티를 사용한다.

#### 문자의 삽입과 삭제
   - insert(:at)
   - insert(contentsOf:at:)
   - remove(at:)
   - removeSubrange(`:)
   - 로 삽입과 삭제를 할수 있다
   
   ```swift
    var cats = "Cat"
    cats.insert("!", at:cats.endIndex)
    print(cats)
    cats.insert(contentsOf: "Super", at: cats.startIndex)
    print(cats) 
    cats.remove(at: cats.index(before: cats.endIndex))
    print(cats)
    let range = cats.index(cats.endIndex, offsetBy: -3)..<cats.endIndex
    cats.removeSubrange(range)
    print(cats)
   ```

#### 부분 문자열
   - 문자열에서 부분 문자를 얻기 위해 prefix(_:)와 같은 서브스크립트 메소드를 이용할수 있는데, 그렇게 구하게된 문자열은 SubString인스턴스이다. 만약 부분 문자열을 단기간에 사용하는게 아니라 장기간 사용한다면 문자열 인스턴스로 바꿔서 사용하는게 좋다.
   - 이는 SubString을 계속 사용하면, 참조를 하게되는 원본 String이 계속 메모리 상에 남아 있게 되어서이다. 일시적으로 사용하는 경우가 아니라면, 차라리 String으로 변환해주면 메모리상 원본이된 String은 더이상 사용되지 않아서 사라진다.

#### 문자열과 문자 비교
   - 문자열과 문자 비교에는 == 혹은 != 연산자를 사용한다.
   - 유니코드는 결합된 문자열을 찾고 비교한다
   - 같은 유니코드 문자여도 유니코드가 다르면 다른 문자로 판별한다.
   - Swift는 문자열과 문자의 비교는 언어를 교려하지않는다. 따라서 언어와 상관없이 같은 문자면 같은 문자로 취급한다.