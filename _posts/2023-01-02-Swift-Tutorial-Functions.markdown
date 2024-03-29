---
layout: post
title:  Swift Function
date:   2022-12-31
image: Swift_logo.webp
tags: [Swift]
---

---
## Swift Function
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 정의와 호출(Defining and Calling Function)
   - 함수를 선언할때 가장 앞에 func 키워드를 붙이고 (person: String)파라미터와 형 그리고 -> String 형태로 반환형을 정의합니다.
   - 간단히, func + func이름 +(변수명: 데이터형) -> 반환데이터형 입니다
   - return이 반환 되므로, 짧은 계산식은 바로 리턴으로 계산과 출력을 같이 해도됩니다.

```swift
func hi(person: String) -> String {
    let hi = "Hello" + " " + person + "!!!"
    return hi
}
print(hi(person: "Cat"))
print(hi(person: "Dog"))
```

### 다양한 타입의 함수

#### 파라미터가 없는 함수(Functions Without Parameters)
   - 입력값이 없이, 원하는 결과값만을 return해옵니다.

```swift
func hello() -> String {
    return "Hello World"
}
print(hello())
```

#### 복수의 파라미터를 사용하는 함수(Function with Multiple Parameters)
   - 여러개의 입력값을 받아서 계산하거나 하는 Func에서 유용합니다.

```swift
func Cat(person: String, CatorNot: Bool) -> String{
    if CatorNot {
        return person + " is cute"
    }
    else {
        return person + " isn't cat"
    }
}
print(Cat(person: "Cat", CatorNot: true))
```

#### 반환값이 없는 함수(Function Without Return Value)
   - C#에서는 Void라 불리는 함수 입니다.
   - 엄밀히 말하면 반환값을 선언하지 않았지만 반환값이 있습니다. 반환값이 정의되지 않았을 뿐입니다.
   - return값은 없지만 print를 통해 앞에서 하듯이 원하는 변수를 출력했습니다.
   - 그러나, print로 함수를 불려오면, return값이 없으니 출력되는 값은 없습니다.

```swift
func hicat(person: String){
    let cast = "Hello " + person
    print(cast)
}
print(hicat(person: "CCC"))
```

#### 복수의 값을 반환하는 함수(Fucntion with Multiple Return Values)
   - 튜플을 함수의 반환 값으로 사용할수 있습니다.
   - 말그대로 여러개의 return값이 나옵니다.

```swift
func Sum(num: Int, num2: Int) -> (sum: Int, overten: Bool){
    let Sum = num + num2
    var overten = false
    if Sum > 10{
        overten = true
    }
    else{
        overten = false
    }
    return (Sum, overten)
}
print (Sum(num:5, num2:3))
```

#### 옵셔널 튜플 반환형 (Optional Tuple Return Type)
   - 위의 반환 값과 달리 반환값에 ?물음표가 붙습니다(옵셔널이 붙습니다)
   - 옵셔널로 반환되었으니, 값에 접근할려면 언래핑하거나 if let같은 옵셔널 체인을 사용하여야 합니다.

```swift
func Sum(num: Int, num2: Int) -> (sum: Int, overten: Bool)?{
    let Sum = num + num2
    var overten = false
    if Sum > 10{
        overten = true
    }
    else{
        overten = false
    }
    return (Sum, overten)
}
if let SumoptionalChain = Sum(num: 5, num2: 3){
    print("\(SumoptionalChain.sum) \(SumoptionalChain.overten)")
}
```

#### 인자 라벨 지정( Specifying Argument Labels)
   - 라벨을 통해 해당 변수를 외부에서 쓸때는 좀더 편하게 작성할수 있게 해둔 요소입니다.
   - 처음에는 이해하기 힘들었으나, 이해하니 정말 좋은 기능인거 같습니다

```swift
func Check(name: String, age: Int, from hometown: Int) -> String {
    let home: String
    switch hometown{
    case 1:
        home = "Busan"
    case 2:
        home = "Seoul"
    default:
        home = "Check Again"
    }
    return "\(name) and \(age)years old and \(home)"
}
print(Check(name: "noranfox", age: 33, from: 1))
```

#### 인자 생략(Omitting Argument Label)
   - 앞에서는 라벨에 또다른 이름을 넣어서 함수사용시 사용하는 이름과 내부이름을 다르게 해주었다면, 이번에는 아예 생략 하는 것입니다.
   - "_"를 이용해서 인자를 생략합니다. 물론 함수선언에서 생략하는것이 아니라, 함수를 다른곳에서 불려와서 사용할떄 생략하는 것입니다.
   - "_"를 선언한뒤 띄어쓰고 변수명을 적어주어야합니다. 붙여적으면 안됩니다.
```swift
func Check(_ name: String, age: Int, from hometown: Int) -> String {
    let home: String
    switch hometown{
    case 1:
        home = "Busan"
    case 2:
        home = "Seoul"
    default:
        home = "Check Again"
    }
    return "\(name) and \(age)years old and \(home)"
}
print(Check("noranfox", age: 33, from: 1))
```

#### 기본 파라미터 값 (Default Parameter Value)
   - 함수의 파라미터 값에 기본 값을 설정할수 있습니다. 함수를 호출해서 사용시, 변수값을 넣지않고 생략해도 기본값이 사용되게 됩니다.
   - 기본 값을 사용하지 않는 파라미터를 앞에 위치 시켜야 사용하기 쉽습니다.

```swift
func Check(_ name: String, from hometown: Int, age: Int = 20) -> String {
    let home: String
    switch hometown{
    case 1:
        home = "Busan"
    case 2:
        home = "Seoul"
    default:
        home = "Check Again"
    }
    return "\(name) and \(age)years old and \(home)"
}
print(Check("noranfox", from: 1))
print(Check("noranfox", from: 1, age: 33))
```

#### 집합 파라미터 (Variadic Parameter)
   - 인자 값으로 특정 형(type)의 집합 값을 사용할수 있습니다.

```swift
func Total(_ nums: Int...) -> Int {
    var total = 0
    for num in nums {
        total += num
        
    }
    return total
}
print(Total(1,2,3,4,5))
```

#### 인-아웃 파라미터 (In-Out Parameter)
   - 인자 값을 직접 변경하는 파라미터입니다. 변수로서 들어온 인자를 변경할수 있습니다.
   - 사용할 인자에 타입 앞에 input을 붙여주면 됩니다.
   - 인-아웃 파라미터는 기본값을 가질수 없고, 집합 파라미터는 input으로 선언될수 없습니다.
   - 인-아웃 파라미터는 return없이 함수 scope 밖에 영향을 줄수 있는 방법입니다.

```swift
var total = 0
func Total(total: inout Int, _ nums: Int...) {
    var sum = 0
    for num in nums {
        sum += num
    }
    total = sum
}
Total(total: &total, 1,2,3,4,5)
print(total)
```

### 함수 형(Function Type)
   - 함수의 형은 파라미터 형과 반환 형으로 구성 돼 있습니다
   - 반환값이 없는 함수로서 사용도 가능합니다.

```swift
func justsum(_ a: Int, _ b: Int) -> Int{
    return a + b
}
print(justsum(1, 3))

func justsumstring(_ a: String,_ b:String) {
    print(a + b)
}
justsumstring("Cat", " is Cute")

```

#### 함수 형의 사용
   - 함수를 변수 처럼 정의해서 사용할수 있습니다
   - 인자의 조건이 동일하다면 아래처럼 선언해서 함수를 변수처럼 사용가능합니다.
   - 인자의 조건을 굳이 선언하지 않아도 Swift가 추론해서 자동으로 함수를 할당 할 수 있습니다.

```swift
var sumFuction: (Int,Int) -> Int = justsum
print("Result : \(sumFuction(5, 10))")

var sumstring = justsumstring
sumstring("Hi"," Success")
```

#### 파라미터 형으로써의 함수 형(Function Type as Parameter Type)
   - 파라미터에 함수 형을 사용할수 있습니다

```swift
func doubleSum(_ justsum: (Int, Int)-> Int, _ a: Int, _ b: Int){
    print("Result is \(justsum(a,b))")
}
doubleSum(justsum, 3, 5)
```
#### 반환 형으로써의 함수 형 (Function Type as Return Type)
   - 결국, 바로 위의 파라미터 형으로서 함수와 이 부분은 함수를 다른 함수의 리턴값이나 인자로서 사용가능하다는게 핵심입니다

```swift
func sum1(_ a: Int, _ b: Int) -> Int {
    return a + b
}
func minus(_ a: Int, _ b: Int) -> Int {
    return a - b
}

func CheckSumOrMinus (check: Bool, a: Int, b: Int) -> Int {
    return check ? sum1(a,b) : minus(a,b)
}
print(CheckSumOrMinus(check: true, a: 5, b: 4))

```

#### 중첩 함수(Nested Function)
   - 위의 함수들은 모두 전역적으로 동작하도록 선언했습니다.
   - 다른 함수 안의 body에서 동작하는 함수가 있는데 이 함수를 중복함수(Nested Function)이라 합니다.
   - 중첩함수는 함수 밖에서는 감춰져 있고 함수의 body내에서 접근 가능합니다.
   - 마치 C#에서 클래스는 클래스내에 클래스가 있고 이는 그 클래스에서만 접근 가능한 모습과 유사합니다.
   - 주어진 예시가 정말 좋은 예시인거같습니다.

```swift
func Last(type: Bool) -> (Int) -> Int {
    func plus(input: Int) -> Int { return input + 1 }
    func minus(input: Int) -> Int{ return input - 1 }
    return type ? minus : plus
}

var currentValue = 4
let moveNearZero =  Last(type: currentValue > 0)
while currentValue > 0 {
    print("\(currentValue)...")
    currentValue = moveNearZero(currentValue)
}
print("zero")
```