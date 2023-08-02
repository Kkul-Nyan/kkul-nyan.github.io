---
layout: post
title:  Swift 프로그래머스 문자열 계산하기
date:   2023-02-28
image: Swift_logo.jpg
tags: [Swift]
---

---
## Swift 프로그래머스 문자열 계산하기
---

```swift
func solution(_ my_string:String) -> Int {
    
    let element = my_string.split(separator: " ")
    var result = Int(element[0])!
    for i in 0..<element.count {
        if element[i] == "+" {
            result += Int(element[i+1])!
        }
        else if element[i] == "-" {
            result -= Int(element[i+1])!
        }
    }
    return result
}
```

각요소들은 띄어쓰기를 통해 구분되어있습니다. 따라서 split를 " " 기준으로 시켜주면 각요소로 나누어집니다 <br>
첫번째 숫자를 기준으로 더하거나 숫자를 빼야하므로 첫번째 숫자를 기준으로 해줍니다.<br>
어차피 첫번째 숫자와 +,= 기호를 제외하면 Int값이기 때문에 강제 언래핑을 해주어도 문제가없습니다<br>
모든 숫자를 부호뒤의 숫자를 더하거나 빼는것이기 때문에 i+1의 기준의 숫자를 더하거나 빼주는 것을 반복해주면 <br>
원하는 결과값을 구할수 있습니다.