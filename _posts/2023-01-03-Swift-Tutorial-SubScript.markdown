---
layout: post
title:  Swift Subscript
date:   2022-12-31
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Subscript
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 정의
   - 서브스크립트는 콜렉션, 리스트, 시퀀스 등 집합의 특정 멤버 엘리먼트에 간단하게 접근할수 있는 문법입니다.
   - 메소드 없이 특정 값을 할당 하거나 가져올수 있습니다.
   - 하나의 타입에 여러 서브스크립트를 정의 할수 있고 오버로드도 가능합니다.
   - 단일 인자 값 말고도 복수 인자 값을 사용할수도 있습니다.

### 서브스크립트 문법 (Sbuscript Syntax)
   - 인스턴스 메소드와 계산된 프로퍼티를 선언하는 것과 비슷합니다.
   - 서브스크립트는 읽고쓰기, 읽기 전용만 가능합니다.
   - getter, setter 방식을 따릅니다.
   - 이는 setter에서 newValue를 사용하거나, get,set을 따로 선언하지 않으면 get으로 동작된다는 의미입니다.

```swift
subscript(index: Int) -> Int{
    get{
        //반환 값
    }
    set{
        // set 액션
    }
}

import Foundation
//자동으로 읽기전용으로 생선된 subscript
struct SelfPlus{
    var number = 0
    subscript(index: Int) -> Int{
        return number + index
    }
}
let SixSelf = SelfPlus(number: 0)
```

### 서브스크립트 사용(Subscript Usage)
   - 새로운 요소를 추가하는데 사용되기도 합니다

```swift
var MoveKey = ["forward": "w", "backward": "b", "right": "d", "left": "a" ]
MoveKey["jump"] = "space bar"
print(MoveKey.count)
```

#### 서브스크립트 옵션(Subscript Option)
   - 입력 인자의 숫자에 제한이 없고, 입력 인자의 타입과 반환타입의 제한도 없습니다.
   - in-out인자나 기본인자값을 제공하지는 않습니다.
   - 오버로딩을 허용합니다.
   - 즉, 원하는 갯수 만큼의 서브스크립트를 선언할 수 있습니다.