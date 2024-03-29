---
layout: post
title:  포스팅 특수효과1
date:   2022-08-25
image: GIT.webp
tags: [github]
---

## 포스팅에서 다양한 글효과 사용하기
---------

<details>
<summary>목차</summary>
<div markdown="1">
[Tweet 사용방법](#tweet-사용방법)  
[1.문단 나누는 방법(줄바꿈)](#1.문단-나누는-방법(줄바꿈))



</div>
</details>

---------

### Tweet 사용방법
원하는 글의 시작과 끝 부분에 <>적어준뒤 tweet을 적어주면  
\<tweet>Cat cAt caT\</tweet> 라 적어주면
<tweet>Cat cAt caT</tweet>
  
  같은 효과가 생기게 된다

----------------
## <span style="color:purple"> **공부하는 식빵맘** </span>  정보 



### 1.문단 나누는 방법(줄바꿈)
  1. 스페이스바 2번+ Enter
  2. \<br>를 사용하는 방법
<br>

### 2. 중접된 구조<br>
  스페이스바 2번 눌러 띄워준 후 작성, 3번 중첩된 줄은 스페이스바 4번 그리고 앞에 '-'+스페이스바

예시
- Hello
  - World  
    - !

### 3. 마크다운 문법을 그대로 보고주고 싶을때는 \\\(역슬러쉬)를 사용한다.
### 4. #에 갯수에 따라 제목 글자 사이즈가 작아진다

예시
# 1번 \#1번   
## 2번 \##2번
### 3번 \###3번
#### 4번 \####4번
##### 5번 \#####5번
###### 6번 \######6번

### 5.텍스트 효과 
  - **강조**   
    - \*\*강조** 할부분에 효과를 줍니다
    - **강조** 할부분에 효과를 줍니다
  - **기울임**  
    - \*기울어진*  효과를 줄 부분을 감싸줍니다
    - *기울어진*  효과를 줄 부분을 감싸줍니다.  
  - **취소선**
    - \~\~취소선~~ 효과를 줄 부분을 감싸줍니다.
    - ~~취소선~~ 효과를 줄 부분을 감싸줍니다.
  - **밑줄**
    - \<u>밑줄\</u> 효과를 줄 부분을 감싸줍니다.
    - <u>밑줄</u> 효과를 줄 부분을 감싸줍니다.  
  - **색넣기**
    - <span style="color:green"> 색바꾸기를 </span> 할 부분에 효과를 줍니다.
<br>

### 6.코드 블록  
  - inline코드 블록
  - 코드에 \```형광펜```같은 모양을 쓰워줍니다.('작은따음표'가 아닙니다.)
  - 코드에 ```형광펜```같은 모양을 쓰워줍니다. 
```
문장,문단에 효과를 줄수도있습니다
```

이사이에 코드를 치면 IDE 편집기같이 코드를 보기 편하게 색이 입혀집니다.
단, \`\`\` 바로 뒤에 **c나 c++를 붙여줘서 c언어를 사용한다고 선언해줘야 합니다.**  

저는 C#을 적어도 효과는 없고, C와C++ 적었을때만 작동했습니다.
```java
using namespace ;

public string Hello;
int main()
{
    consolo.Writeline("Hello"); //c대신 java를 넣어도됩니다.
}

```

\`\`\`로  감싸져서 효과가 생기면, **내부에  markdown효과를 사라집니다**.

<u>중첩 구조 없을 때</u> 스페이스바 4번을 문자을 앞에써주면 그문장은 자동으로 **inline효과**가 생깁니다.

스페이스 4번입니다.

    스페이스4번으로 효과주기

### 7. 링크
```
1.<https://noranfox.github.io>
2.[NoranFox blog](https://noranfox.github.io)
3.[Tweet 사용방법](#tweet-사용방법)
``` 



  - 1.링크주소 그대로 링크하기
    - <https://noranfox.github.io> 링크가 걸렸습니다.
  
  - 2.특정 단어나 문장에 링크걸기
    - [NoranFox blog](https://noranfox.github.io) 블로그 부분만 링크가 걸렸습니다.
  
  - 3.목차만들때 유용한 문장 링크걸기  
    - [Tweet 사용방법](https://noranfox.github.io/2022/08/25/tweet/)
    헤더에서 몇개의 #을 사용한지 중요하지않다. 오직 ###였어도 #면 충분하다.

### <span style="color:red"> ~~8.인용문~~ </span>
  - \>로 표현 가능, \>>는 중첩 인용문. 중접구문부터 만들어줘야하니 스패이스2번+\>>
  ```
  >C#  
    >>List  
  ```  
>C#  
  >>List  

  - 출처남기기 -> \<cite> --- 와 {{: .small}}로 인용문 출처를 남길수있다  

```
<cite>Steve Jobs</cite> --- Apple Worldwide Developers' Conference, 1997
{: .small}
```

<cite>Steve Jobs</cite> --- Apple Worldwide Developers' Conference, 1997
{: .small}

<br> 

### 9.리스트  

  - 중첩구문을 이용한 리스트

```
- C#  
  * Program  
    + List  
  * Program2  
- C
```

- C#  
   * Program  
     + List  
   * Program2  
- C
<br>
- 순서를 넣은 리스트 
  - 띄어쓰기 3칸씩 해줘야한다

```
1. C#
2. Program
  1. List
    - first
    - second
  2. Dictionary
    - first
    - second  
3. Finish
```

1. C#
2. Program
   1. List
     - first
     - second
   2. Dictionary
     - first
     - second  
3. Finish
  
### 10.Check List
  - \- 스패이스 [스패이스] 스패이스 내용 주의할것

```
- [ ] 체크 안됨
- [X] 체크 됨
```

- [ ] 체크 안됨
- [X] 체크 됨

### 11.표(Table) 만들기
  - \| 와 -(3개이상)의 조합으로 테이블을 만들수 있다.  
    - 정렬
      - 왼쪽정렬 \|\:-\|
      - 오른쪽정렬 \|\-:\|
      - 가운데정렬 \|\:-:\|
```
|**이름**|나이|특이사항|
|:---:|---:|:---|
|홍길동|20|조선시대|
|김철수|25|근현대|
|홍길동|23|정보X|
```


|**이름**|나이|특이사항|
|:---:|---:|:---|
|홍길동|20|조선시대|
|김철수|25|근현대|
|홍길동|23|정보X|


### 12.이미지 삽입

  - !를 앞에 붙여준뒤 링크하듯이 해준다. 미리 혹은 같이 에셋폴더에 이미지를 넣어서 git에 올려주면된다.

```
![cat]({{ site.baseurl }}/images/20220826/cat.webp)
```

![image]({{ site.baseurl }}/images/20220826/cat.webp)

  - 이미지 사이즈 조정하기
    - 이미지 명령어 뒤에 {: width="  " height=" "}붙여주면된다.

```
![image](assets/img/icons/github_icon.webp){: width="100" height="100"}
```

![image](assets/img/icons/github_icon.webp){: width="100" height="100"}


### 13.토글 리스트 만들기
  - 마크다운에서 지원하지않고 html를 details태크로 사용

```
<details>
<summary>토글</summary>
<div markdown="1">

토글내용

</div>
</details>
```

<details>
<summary>토글</summary>
<div markdown="1">

토글내용

</div>
</details>


### 14. 맨 위 이동 버튼
  - 링크부분을 \#으로 두면 맨뒤로 이동

```
<a href ="#" class = "btn--success">Button1</a>
```

<a href ="#" class = "btn--success">Button1</a>


```
[Button2](#){: .btn .btn--primary }
```

[Button2](#){: .btn .btn--primary }


----------------