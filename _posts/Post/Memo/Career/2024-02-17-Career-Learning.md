---
title: "Career-Learning"
# description: ""
categories: [📀Post, 🍋‍🟩Memo]
tags: [Memo, Learning]
image: "/assets/img/background/20230112_151539.jpg"
hidden: true

date: 2024-02-17. 01:40
# last_modified_at: 2024-02-21. 05:58
# last_modified_at: 2024-02-24. 03:49
# last_modified_at: 2024-03-05. 16:29
# last_modified_at: 2024-03-06. 05:18
# last_modified_at: 2024-03-12. 14:20
# last_modified_at: 2024-03-20. 06:01
# last_modified_at: 2024-03-27. 17:58
# last_modified_at: 2024-04-03. 13:30
# last_modified_at: 2024-04-18. 20:13
# last_modified_at: 2024-04-27. 13:53
# last_modified_at: 2024-07-11. 21:45
# last_modified_at: 2024-08-06. 23:09
# last_modified_at: 2024-08-12. 11:21
# last_modified_at: 2024-08-19. 16:30
# last_modified_at: 2024-08-26. 11:39
# last_modified_at: 2024-08-27. 22:06
# last_modified_at: 2024-09-14. 16:57
# last_modified_at: 2024-09-14. 21:06
# last_modified_at: 2024-10-21. 12:14 # Job, Career, Interview 정리
# last_modified_at: 2024-11-13. 03:33 # -PS
# last_modified_at: 2024-11-13. 07:44 # -CG
last_modified_at: 2025-03-15. 07:00 # Learning -> Career Learning, '배움'에 내한 내용은 Learning으로
---

## 📀 리마인드

---

- PS - 코딩 테스트/알고리듬
- 면접에서 답할 정도의 그래픽스

- CS/면접
- 유데미 언리얼 강의
- 게임 수학, 물리, 영어
  - 기본적인 행렬, 벡터의 내적과 외적
  - 기본 뉴턴 역학정도는 -> 선형대수 개념 없이 벡터와 스칼라를 크기와 방향, 크기만 있는 물리량으로만 이해 X

## 📀 프로젝트

---

- 면접, 포폴 관련 질문 준비
- "이 기능은 어떻게 구현하셨나요?", 단순 열거 보다는 경험과 함께 설명. "~를 몰랐는데 공부하게 됐습니다"
- 어떤 최적화 기법을 적용했는지

- 하나의 기승전결 완성작보다는 효율적 로직, 기능구현에 포커싱
- 게임 엔진 경험은 프로젝트의 핵심이 아니다. 프로젝트에서 강조할 점은 프로젝트를 통해 전반적인 게임 제작 프로세스와 타 파트가 하는 업무를 이해, 다양한 문제를 슬기롭게 대처한 경험.
- -> 문제 해결자로서 팀에 기여한 내용들을 잘 기록.
  - 콘텐츠 제작/엔진 활용보다 프로그래머로서 프로젝트에 기여할 수 있는 꼼꼼한 관리, 효율성 추구에 대한 마인드가 중요
  - i.e. 커뮤니케이션을 위해 노트 정리를 꼼꼼하게 하고 공유한 경험, 실수에 의한 발생한 문제를 감지하는 이중 시스템 개발
  - 확장성, 기획자가 있다는 가정하에 만든, 프로그래밍을 거의 모르는 사람이 모든 값을 조정 가능한, 에디터/엑셀 파싱
- 깃, 다른 사람 코드 분석
- 게임 엔진 활용 능력
  - 엔진 능력은 어차피 다시 배운다. 회사 프로젝트에 따라서 재조립된다. -> 기본에 충실하자
  - 기술적으로 어필할 수 있는. 프로젝트를 진행하면서 포폴 정리, 계속 자그만한 시스템들을 만들어나가야 한다.
  - 게임 엔진 활용 기술을 어필하고 싶다면, 에디터 툴 확장. 툴을 활용해 생산성 개선 고민해보는 경험.

## 📀 CS / 면접

---

- 대답은 알고있는 선에서, 모르는건 모른다고

- Effective C++
- C와 C++의 차이?
- 코테 알고리듬 질문, 게임 특화 알고리듬 종종 (A*, QuadTree, BSP)
- 코드에 대한 힙과 스택의 레이아웃이 그려져야. 생성자 소멸자 호출 순서, 컴파일 타임과 런타임 관점을 명확하게 파악.

- [질문 리스트](https://github.com/Romanticism-GameDeveloper/GameDeveloper-Client-Interview?tab=readme-ov-file)  

- 배열과 리스트(벡터)의 차이, 본인이 알고있는 게임 최적화 방법
- @ 면접 마지막에 궁금한거 있냐고 물어볼때는 이론은 좋은데 실제로 적용하기 어려운 걸 어떻게하고 있는지 물어본다면
  - 클라이언트에서 유닛테스트 어떻게 적용하고 있는지, A/B 테스트라든지, 유니티 씬 충돌나면 어떻게 처리하는지

## 📀 _

---

- 코테
  - 문제 이해하기
  - 데이터와 문제에 맞는 알고리듬 찾기
  - 알고리듬 적용하고 디버깅하기
    - DFS 쓸 때는 스택쓰기
    - DFX 쓸 때 시작지점 stack에 미리 넣기

### 💿 시스템 프로그래밍

- 멀티플랫폼 대응을 게임 엔진이 다 해주다보니..
- 서비스를 운영하기 위해서는 시스템에 대한 지식이 필수적이라 중요

- '뇌를 자극하는 윈도우즈 시스템 프로그래밍', 'Advenced! 리눅스 시스템 네트워크 프로그래밍', 'OS, 컴퓨터 구조론'

### 💿 멀티 쓰레드 프로그래밍, 비동기 프로그래밍

- 이건 뭘로 공부하지..?

### 💿 네트워크

- 서버에서 여러 개의 요청을 동시에 처리하기 위한 방법
  - Thread
    - Lock
    - DeadLock
  - Microthred (Coroutine, Fiber)
    - 장단점을 아아야 겠죠

- 서버에서 여러 연결을 효율적으로 처리하는 방법
  - IOCP
  - epoll

- TCP, UDP
  - 어떻게 동기화를 할 것인가
  - 메시지를 어떤 방식으로 보낼것인가 (Serialization)
- 네트워크를 아는 것과 서버 프로그래머로의 능력을 갖추는 것과는 결이 다른 이야기
- 서비스 관점에서 네트워크/DB 어떻게 동작하는지 이해 필요. i.e. AWS 기반 DB 연동 가벼운 웹사이트 및 관리도구
- TCP소켓 기반의 실시간 게임

- 소켓 (윈도우즈 기반)
  - 기본 소켓 프로그래밍, IOCP
  - boost::asio?
- 웹

### 💿 DB

- Transaction
- SQL
- Stored Procedure
- NoSQL
  - Redis

- 주요 데이터베이스 기술 두 가지
  - ㅡ 관계형 데이터베이스 Relational
  - ㅡ 문서 " Document

- 최소한의 항목
  - 관계형을 익숙하게 다를 능력
  - 문서에 대한 기초적인 이해 정도는
  - _
    - ㅡ 데이터베이스 작동 방법
    - ㅡ 데이터를 얻기 위해 단순한 쿼리를 수행하는 방법
    - ㅡ 데이터 삽입, 업데이트, 삭제하는 방법
    - ㅡ 데이터 세트 조인하는 방법
    - ㅡ 자신이 선택한 플랫폼이나 프레임워크에서 코드를 사용해 데이터를 가져오거나 저장하는 방법 ㅡ 데이터베이스와 연동되는 코드

관계형 DB에 대해 배우면 SELECT 문 작성이 그 20%에 해당한다는 걸 곧바로 깨닫는다.  
또한 테이블 Table을 조인 Join하는 방법을 배워야 한다는 것도 곧 깨닫게 된다.  
관계형 DB의 모든 기능을 배워야 한다는 거도 곧 깨닫게 된다.  
관계형 DB의 모든 기능을 배우려고 시간을 낭비하기보다 SELECT 문을 쓰는 법, 테이블을 조인하는 법 등 핵심적인 20%를 배우는 데 집중하라.  

### 💿 _

- 데이터 베이스
  - SQL 문
  - Index에 대한 기본상식
  - Redis?

- 헤테로지니어스
- DApp
- DTO
- 고포류

- 채팅 서버 - 실시간? C++
- 로그인 - API 서버? 웹서버? 비실시간 통신? ASP.Net Core Web API

- Win32 API 기본은 아는
- 네트워크 라이브러리를 사용하는 프로그램은 간단한 것 (채팅 프로그램)

- 온라인 보드 게임 (오목, 장기등)
- 온라인 액션 캐주얼 게임

- IOCP를 핵심 포폴로 하고 싶다면
  - 만든 라이브러리를 사용한 게임 서버를 만들어야됨
  - 더미 테스트 필요
  - 벤치마크 수치 제시

- 멀티스레드 프로그래밍 Lock-Free
  - 이미 락 프리 알고리듬을 사용한 컨테이너는 여러 개 나와 있음, 직접 만들 필요 없고, 만들면 겁남

- 오픈 소스 참고

- pure virtual function, smart pointer
- 힙메모리는 어떤 경우에 사용되며 어떠한 특징을 가지고 있는지
- 쓰레드의 장점과 단점

- win32 api는 메시지 루프 작성할 수 있고 마우스 키보드 메시지 처리할 수 있을 정도면 됩니다
- 일반적으로 게임 클라이언트 개발에 필요한 win32지식은 링크하신 강좌 정도면 충분합니다. 더 필요하면 찾아보고 학습하면 됩니다.
  - <https://youtu.be/V9nwIepvPWc?list=PLXvgR_grOs1CyJDnWeUTqbmKG1VFQM72e>
  - <https://youtu.be/8DkgVJOBzhs?list=PLXvgR_grOs1CyJDnWeUTqbmKG1VFQM72e>

- 엔진에서 쓰인 C++에 대한 지식
  - OOP 개념
    - 상속
    - 다형성
    - 가상함수
  - 템플릿
  - STL

- 메모리 관련 지식
  - 스택
  - 힙
  - 메모리 풀
  - 스마트 포인터

- <https://www.inflearn.com/course/시스템-프로그래밍>
- Async/Await과 코루틴의 차이는?
- c# 참조 스마트포인터
- C#의 특징(특히 가비지컬렉터), 배열과 리스트(벡터)의 차이, 본인이 알고있는 게임 최적화 방법
- partical 클래스
- 가비지 컬렉터
- 포폴에 어떤 최적화 기법을 적용했는지
- a/b 테스트, 유닛 테스트
- 멀티쓰레드, 파일입출력

- 왜 OOP
- 왜 Functional
- 왜 쓰레드
- 왜 비동기
- 정도의 이야기는 딱 한 문장으로 설명이 가능하고, 업계인들끼리도 모두가 납득하는 한마디가 있어야 할 것 같은데,

- 데디서버와 그래픽스에 대한 요구 능력
- 데디서버 (Dedicated Server)
- 데디서버는 특정 게임이나 애플리케이션의 서버 측 기능을 처리하는 전용 서버

- 서버 관리 및 운영: 서버의 설치, 설정, 유지 보수 능력.
- 네트워크 이해: 네트워크 프로토콜, TCP/IP, UDP 등에 대한 이해.
- 프로그래밍 언어: C++, C#, Python 등 서버 개발에 사용되는 언어에 능숙.
- 성능 최적화: 서버의 성능을 분석하고 최적화하는 능력.
- 보안: 서버의 보안 문제를 식별하고 해결하는 능력.
- 데이터베이스 관리: SQL, NoSQL 데이터베이스의 운영 및 관리 능력

- 함수형 프로그래밍
- 데이터 지향 프로그래밍
- CBD 개발 방법론
- CI/CD : Github Actions
- Jenkins, Jira와 유사한 환경을 다뤄본 경험이 있습니다. (Github Action, Github Project)
- OOP
  - OOP의 개념
  - OOP의 요소
  - SOLID

- CS
  - 자료구조
  - 디자인패턴
    - 공통적으로 발생할 수 있는 문제에 대한 재사용가능한 솔루션/해결책
    - 옵저버 패턴
    - 싱글턴 패턴
    - 오브젝트 풀
    - FSM
    - BT
- 유니티
  - 에셋번들
    - 무엇인지
    - 어떻게 사용하는지
    - 왜 사용하는지
  - 에디터 프로그래밍
    - 사용해보셨는지
    - 그게 무엇인지 설명해주세요
  - 쉐이더 기술
  - 최적화 기술
  - ScriptableObject
    - SOHelper, SOManager
  - 코루틴의 과정
    - 시작
    - yield를 만나면 원래 함수로 돌아감
    - 종료

- C#
  - IEnumerable
  - 리플렉션
  - GC

- 프로젝트
- 플레이팹
- 이펙트 쓸 수 있는지

- Gpgs 인앱결제 광고 등 외부플러그인 같은 기능
- 내외적 짐벌락 사원수
- 유니티 설계 경험 기록
- Dotween
- 클로저
- 앱 출시 경험 Relay적용 경험
- Dx
- 개발 문서화?
- 리드미 파일, 코드 주석, 릴리스 파일
