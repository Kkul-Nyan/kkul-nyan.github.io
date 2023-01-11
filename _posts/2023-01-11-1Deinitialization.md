---
layout: post
read_time: true
show_date: true
title:  Swift Deinitialization
date:   2023-01-11
description: about Deinitialization
img: banner/Swift_logo.jpg
tags: [Swift]
author: Noranfox
github:  noranfox/
mathjax: yes
---

---
## Swift Deinitialization
---
\* 스스로 공부 및 정리를 위해 [The Swift Language Guide](https://jusung.gitbook.io/the-swift-language-guide/)을 요약 및 정리 한 내용입니다. 

### 초기화 해지 (Deinitialization)
   - 초기자와 반대로 클래스 인스턴스가 소멸되기 직전에 호출됩니다.
   - deinit 키워드를 사용합니다.
   - 오직 클래스 타입에서만 사용 가능합니다.

#### 초기화 해지의 동작 (How Deinitializaion Work)
   - 보통 Swift가 자동으로 자원의 해제 하지만, 열었던 파일을 사용이 끝나고 닫는 등 사용자가 자원해지를 소동으로 작업해야하는 경우도 있습니다.
   - 클래스당 오직 하나만 선언할 수 있고 파라미터를 받을수 었습니다. 
   - deinit{ } 형식입니다.
   - 자동으로 호출되고 수동으로 호출할수는 없습니다.
   - Superclass의 Deinitialization은 subclass에서 선언하지 않아도 자동으로 호출됩니다.
