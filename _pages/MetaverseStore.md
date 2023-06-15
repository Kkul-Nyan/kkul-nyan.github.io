---
layout: page
title: MetaverseStore
permalink: /MetaverseStore/
image: Metaverse.png
---

# MetaverseStore

개발 환경: Windows10+, Mac Ventura<br>
개발툴: Unity 2020.03.37f1, Adobe Substance 3D 2022, Blender 3.0<br>
게임 이름: MetaverseStore<br>
게임 장르: VR 쇼핑<br>
기획 의도: 휴대폰의 쿠팡, 인터넷의 네이버스토어같은 메타버스의 온라인쇼핑중개플랫폼<br>
작업 기간: 22.08.01 ~ 22.11.20<br>
프로젝트 완료일: 2022년 11월 20일<br>
플랫폼: 오큘러스퀘스트, PC<br>


![metaverse1]({{ site.baseurl }}/images/Metaverse/metaverse1.png )

![metaverse2]({{ site.baseurl }}/images/Metaverse/metaverse2.png )

- 기술 총괄 : 이서희
- 기획 총괄 : 최미수
- 운영 총괄 : 정현기

## 0-1. 주요작업

![02]({{ site.baseurl }}/images/Metaverse/02.png )
![03]({{ site.baseurl }}/images/Metaverse/03.png )

1. 주간회의 PPT작성 및 Notion일정관리
2. 그래픽스 최적화(Lightingmap, URP 작성)
3. ManagerProgram(입점업체용 PC프로그램 - 데이터연동 및 오브젝트 배치, 상점이름 및 상점 오브젝트설정)
4. AWS DymanoDB연동 → SDK충돌로 인해 Azure Playfab으로 변경
5. G-Star용 뽑기컨텐츠
6. G-Star용 컨텐츠 오락실룸 씬, 오브젝트 제작 및 텍스처 제작
7. G-Star용 컨첸트 폭죽 Particle 제작

## 01.계획일정

- 8월 전체적인 프로토타입 완성
- 9월 수정 및 구체화
- 10월 완성시키기

## 02.**필요한 중요한 기술**

### 2-1. 주 사업이 번역이 있으면 효율이 좋은 산업에 활용하라.

### 2-2. 자기 회사제품을 3D화 해서 소개할 수 있는 산업에 활용하라.

### 2-3. 전시회 같은 것으로 활용하라.

- 화면공유 필
- 판매하고자 하는 제품의 3D 모델링을 화면에 표현
- 번역프로그램 (파파고, 구글) 를 이용해 실시간 번역이 가능 / 실시간 채팅번역
- 웹RTC 혹은 Agora.io를 이용해서 화상, 음성 띄우기
- Photon Server에 대한 이해

## 03. 부가적 기술

- FBX 파일을 배치시키기 (전시회)
- Open CV를 이용한 얼굴인식 (캐릭터에 얼굴을 입히는 방식) / 자기만의 캐릭터 만들기
- 각 Room에 맞는 분위기 조성

## 0**4. Scene 구성 및 필요 기능**

### 01.Intro : 주위를 구경할 수 있게하고 입구에 UI구성

- 로그인/회원가입/입장, 가상키보드 구현 / 주요 스크립트 : Intro Manager.cs

### 02.Server : 복도를 걷다가 각 기업의 매장을 구성

- ( A / B / C Company ) 원하는 기업 선택 후 Join Room 클릭시 다음 03 Scene 이동
- 주요 스크립트 : Server Manager.cs

### 03.Lobby : 각 기업의 특성에 따라 카테고리(방 제목) 분류 한 룸 생성 (최대 인원 설정 필요)

- BackGround에 깔끔한 이미지 혹은 기업이미지
- 주요 스크립트 : Lobby Manager.cs, Information.cs, LobbyCount.cs, Data.cs

### 04.Show : 기업의 전시회장 및 회의장

- 회의공간에서 화면공유 및 번역 구현하기 / 전시장에서 제품 상세 설명페이지로 이동, 구매 구현하기
- 주요 스크립트 : PlayerMove.cs, GameManager.cs, DetailManager.cs, ButtonManager.cs, ~

### 05.Detail : 제품의 상세 모델링 Scene

- 제품을 상하좌우 늘리기 줄이기를 할 수 있게 하기
- 주요 스크립트 : SizeManager.cs
- 모든 Scene에는 뒤로가기 버튼 UI 필요 (LeaveManager.cs)

## 05.진행사항

### 8월 1주차 목표 : 방을 구성, 보이스챗 가능하게 하기, 캐럭터 움직이기, 화면공유

### 1주차 발표 내용 : 개론, 2주 뒤의 결과, 핵심기술, 게임성 컨텐츠 요소

### Week 1-1

- Photon Setting을 통해 회원가입 / 로그인 로그인 시 Lobby로 이동
- Photon Lobby 구현 / 이름, 지역 입력 후 Room 이동
- Photon Room 구현 / 방 생성, 최대 인원, 방파괴 설정 Game 이동
- Photon Game 구현 / 대면 할 수 있는 공간마련
- 추가해야 할 과제 : Photon Game에서 나가기 기능
- 앞으로 해야할 과제 : Photon server 심화, 파파고 API 공부, 웹RTC에 대한 공부

### Week 1-2 (수정해야 할 사항 있음.)

- Photon Game Scene에 Window Screen 화면 공유 구현 (다른 스크린 공유도 가능 / 활용 방안 생각해보기)
- Photon Game Scene에 Exit 버튼 (수정 해야할 부분 : Master가 없어지는지 재접속시 화면공유가 없어짐.)
- Photon Game Scene의 채팅창 글씨크가 해상도 강제 조절 후 이상해짐 (수정 요망)
- 기존 UI 조금 수정
- 디스코드 회의 내용
- Photon 서버 기능, Script에 적용되는 명령어 이해하기
- 파파고 API 기능 적용하기
- 3D 제품 업로드 가능하게 하기
- PC, 모바일, VR 연동 가능하게 하기 (현재 Zoom은 PC와 모바일이 연동이 가능하다.)
- 플랫폼에 대한 해상도 적용하기
- 방 구성을 좀 더 다양하게 하기
- 현재 나와있는 Zoom(성민), Google 미팅(서희), 디스코드(미수), 팀뷰어, MicroSoft Teams(현기)에 대해서 조사해보기

### Week 1-3

- 프로젝트 시작
- 추가했으면 하는 사항 : 채팅방에 입장/퇴장 표시 (색을 이용해서 눈에 띄게), 현재 인원 보이게 하기
- 사용자 간의 최적화가 필요하다 (매우 중요)
- 모르는 사람이 접근을 해도 UI/UX 부분에서 충분히 설명이 필요하다
- 다른 플랫폼이 가지지 않은 차별점을 비교 분석하면 더 좋을 것이다

### Week 1-4

- Google Translate API 적용해보기 (~작업중)

### Week 2-1

- Unity version 다운 후에 Room에서 Game이 안들어가는 버그 발생 (~수정중)
- API 적용시 너무많은 UI들이 존재 줄일 방안 검토
- 컴퓨터, 안드로이드 버전 / VR 버전을 나누어 만든 후에 만나지게 하기 (공부 중)

### 8월 2주차 : 3,4주차 목표 VR를 중점으로 한 ShowRoom 새로만들기 / Scene 구성, Photon 연동, 3D 모델링 업로드 하기 (PPT 자료)

### Week 2-2

- 팀원과 상의 후 현재 프로젝트를 갈아 엎고 VR로 가상 전시회 구성하기
- 참고 : VR CHAT 전시, XR interaction, ShowRoom 구성, Photon Server
- 구현 할 기술 : 결제 시스템, Charactor 번역, 가상공간에서의 3D modeling 보여주기
- 
    
    ![04]({{ site.baseurl }}/images/Metaverse/04.png )
- 
    
    ![05]({{ site.baseurl }}/images/Metaverse/05.png )
- 
    
    ![06]({{ site.baseurl }}/images/Metaverse/06.png )
- 
    
    ![07]({{ site.baseurl }}/images/Metaverse/07.png )
- 
    
    ![08]({{ site.baseurl }}/images/Metaverse/08.png )
    

### Week 2-3

- Android, Oculus Quest2 세팅으로 새롭게 만들기
- 01.Intro Playfab으로 회원가입, 로그인 하게 하기 / Photon 연동
- 02.Server A B C Company를 선택하고 접속하게 하기
- 03.Lobby 각 Company의 로비에 접속
- 04.Show 메인 전시장/회의실이 있는 ShowRoom에 접속
- Canvas 를 WorldSpace로 구성, UI 맞춰넣기 (쉽지 않음.)
- Blender로 각 Scene에 맞는 모델링 하기

### Week 2-4

- 04.Show Scene에 Charactor 만들기 (완료) / 제품 설명 UI 띄우기 / 05.Detail Scene Load 필요
- 05.Detail Scene 필요 (제품 상세 모델링)

### 8월 3-4주차 토론, 해결해야하는 내용 Scene 별로

- 전체적 문제 : Scene UI배치, Prefab Modeling, VR Controller 띄우기
- 01.Intro : 로그인 UI를 클릭시 나타나게 하기
- 02.Server : UI 위치에 따른 마우스 클릭 위치가 다름. UI 위치 조정 필요
- 03.Lobby : UI를 두개로 구성? 1. 방 리스트 UI 2. Join, Create UI
- 04.Show : 캐릭터가 VR로 움직여지는지 / 사진들 마다 UI 배치, 버튼 클릭시 다음 Scene로 넘어가기, 결제 UI 띄우기 / 제품 상세 설명 UI 만들기
- 05.Detail(1~5) : 제품 3D 모습을 볼 수 있게 배치하기

### Week 3-1

- Scene 블랜더 프리팹 입히기 UI 위치 고정하기
- 구글 API 결제 시스템 도입하기
- VR로 실행 가능하게 하기 ( 3.6에선 됐는데 3.5에선 안되는 중 )

### Week 3-2

- UI 위치 조정 완료
- 구글 API 결제 시스템 넣기 완료
- VR로 실행 가능하기 완료 (2020.3.37f1으로 다운 그레이드)
- VR Keyboard 넣기

### Week 4-1

- Build & Run 시 수정사항 대수 / 오류는 어떻게 해쳐 나갈 것인가?
- 01.Scene VR Keyboard Ray 먹히지 않음, 키보드로는 먹혀서 04.Show 에 캐릭터끼리 만나지는가 확인해 볼 것.
- Charactor의 기본 Transform 위치를 지정하기 Script는 짜놓았음 되는지 확인해 볼 것.
- 04.Show 모델링 된 물건을 캔버스에 올리기 어떻게 할 것인가? Fbx 파일을 집어 넣을것인가?
- 추가적 서버안정화 부분, 결제시스템 창이 뜨는가 다시 확인하기.

### Week 4-2

- 모든 Scene에서의 VR Keyboard 수정 완료.
- Scene을 대폭 줄여보기 Lobby와 Room 생성사이 불필요 Scene 있음. (제거 완료)
- 01.Scene에서 서버까지 Connect 하고 02.Lobby를 로비로 바로 만들기. (완료)
- 모든 Scene 꾸미기

### Week 4-3

- Scene : 높은 산 뷰에서 버스를 타고 부산 바다로 가는 모습으로 표현
- Scene : 상점들을 배치 / 광안대교와 광안리 앞바다 모습을 최대한 표현
- Scene : 각 상점들의 주제를 정해서 3가지로 배치 (Watch Shop, Car Shop, Furniture Shop)
- Scene : 제품들을 구경할 수 있고, 구매 할 수 있는 전시관(샵)으로 구성
- 각 Scene에 텔레포트 필요, 03. Scene은 캐릭터가 인스턴트 되는지 봐야 함.

### Week 4-4

- 소비자 / 구매자 두 가지의 빌드를 해서 소비자와 구매자를 구분필요.
- 소비자는 구매 및 제품 구경이 가능 해야하고, 공급자는 제품 배치 및 판매 등록을 할 수 있어야함. (AWS DB 이용 할 예정)
- 구글 번역 및 TTS를 통해서 번역 및 번역한 말을 TTS로 나오게 해야함. (구글 번역 성공)

### Week 5-1

- 소비가 / 구매자 두 가지 빌드 완성 (AWS는 오류가 있어서 Playfab DB로 구성)
- Asset 구매 완료되면 해결 될 문제 들 다수

## G-Star 성과 동영상

<iframe src="https://www.youtube.com/embed/wd_4NDNlspM" frameborder="0" allowfullscreen></iframe>