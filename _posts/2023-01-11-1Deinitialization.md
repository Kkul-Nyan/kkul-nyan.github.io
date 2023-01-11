---
layout: post
read_time: true
show_date: true
title:  Swift Deinitialization
date:   2023-01-10
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