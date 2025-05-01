---
title: "Witch Mendokusai"
description: "게임 개발 프로젝트"
categories: [🫐WitchMendokusai]
tags: [WitchMendokusai]
image: "/assets/img/post/works/_witch-mendokusai/screenshot/240618-000000.png"

date: 2023-06-01. 10:25
# last_modified_at: 2023-06-01. 10:25
# last_modified_at: 2023-10-11. 17:13
# last_modified_at: 2023-11-22. 08:07
# last_modified_at: 2023-11-29. 13:12
# last_modified_at: 2023-12-02. 15:41
# last_modified_at: 2023-12-05. 08:42
# last_modified_at: 2023-12-07. 07:52
# last_modified_at: 2023-12-25. 03:09
# last_modified_at: 2024-01-15. 19:53
# last_modified_at: 2024-01-25. 05:21
# last_modified_at: 2024-02-01. 09:34
# last_modified_at: 2024-02-03. 05:23
# last_modified_at: 2024-02-04. 18:12
# last_modified_at: 2024-02-08. 05:13
# last_modified_at: 2024-03-07. 17:27
# last_modified_at: 2024-03-08. 20:58
# last_modified_at: 2024-03-10. 14:00
# last_modified_at: 2024-03-12. 10:09
# last_modified_at: 2024-03-14. 02:39
# last_modified_at: 2024-03-17. 13:06
# last_modified_at: 2024-03-18. 16:12
# last_modified_at: 2024-03-18. 18:37
# last_modified_at: 2024-04-03. 14:39
# last_modified_at: 2024-04-08. 19:45
# last_modified_at: 2024-04-10. 11:15
# last_modified_at: 2024-04-18. 11:31
# last_modified_at: 2024-04-30. 05:05
# last_modified_at: 2024-05-05. 11:04
# last_modified_at: 2024-05-22. 20:49
last_modified_at: 2025-04-29. 06:38 # 프로젝트 문서
---

_
{% include embed/youtube.html id = "h1iQhfBtNLo" %}

## 📀 머리말

---

### 💿 참여 / 담당

### 💿 사용한 툴

- Unity 6
- VS Code
- Aseprite
- FMOD
- Github

## 📀 Todo

---

### 💿 Task 1

- Sprite -> 3D 모델

### 💿 Task 2

- AI
  - 전투 AI 몬스터, 동료 AI (멀티에도)

### 💿 VFX Graph

### 💿 _

시너지?  

- 사실과 변수
  - 개념적
  - 골드, 마나 계속 변동하고

[Playables0](https://youtu.be/12bfRIvqLW4)  
[Playables1](https://youtu.be/nn3SnfNNEmk)  

카메라 회전  
공격 조이스틱  
카메라 시점 변경 스크롤 (롤, 이리 휠 스크롤)  

조합 - 제작 - 아이템/위상 - 상점  
골드 수요 - 세금, 타이쿤류 Like 쿠키런 킹덤  

- 다듬어야 할 것들 (후추)
  - 메인 화면
  - NPC 마커
  - NPC 대화
  - 전투 결과 화면
  - 전환/트랜지션 시 코루틴
    - 전투 진입 시 아이캐쳐
    - 블루 아카이브 스킬 같은
    - 로그라이크 죽음을 맵 별로 다른 엔딩이나 컷신 등으로?
      - 템플런
    - 포켓몬 게임 인트로
  - 지역 입장 UI (201번 도로)

- WIP
  - 행동트리 (에디터, ViewGraph)
  - 에디터
    - SO 정렬 기능
    - 에셋 선택창도 커스텀 할 수 있으려나?
    - 몬스터 스폰, 드롭 테이블?
    - 에셋 버퍼 관리
    - 그러면 에셋 생성할때 고유한 ID 테이블을 미리 정해둬야 편하겠네
    - 저장 데이터 관리 -시각화 수정, 세이브/로드
    - 맵 관리? 지도?
  - 상호작용
    - NPC
      - 떠상
        - 던전 떠상 (런 능력치?)
        - 떠상 (설계도?)
    - 제단
    - 상자, 미믹
    - 동전
    - 유적 버튼
    - 해골
    - 제단
    - 폭발하는 오브젝트
    - 돌탑

- 고민해봐야 하는 것들
  - 아이템 드롭 , 자동 획득이 아니라 z 눌러서 먹게
  - 몬스터 마다 성격이 있다 Like 팩맨
  - 플라스크

- 던전
  - 로그라이크 (던그리드 형식? or 슬더슬 라이크나 위치 그거 처럼)
  - 보스 연출
  - 보스 행동패턴
  - 전투 시스템
  - 전체적인 던전 구조 (절차적?)
  - 던전 제약
  - DungeonLoop
  - 던전 보상
  - 몬스터
  - 인게임 재화로 리롤 (제한, 최대 등급 - 1 천장)

- Must
  - 어드레서블 서버로 해야겠는데, 플레이 가능하게 하려면
  - 데미지 연산
  - 아이템 강화 (강화 재화)
  - 마을 의뢰, 메인 퀘스트 (마법 책)
  - 대화 스크립트

- 명령어 (테스트/디버깅)
- NPC Waypoint 이동 경로
- 게임 시작할 때 동숲처럼 집에서 나오는 걸로 시작할까?
- 우체통 있으면 재밌겠다
- 시간 개념을 둘까?
- 조작키 방향키에 Ctrl Alt , Z?
- 전투 끝났을 때 데미지 받지 않도록
- 타임라인 이용한 연출?
- 길찾기? a*?
- Json, Playfab, Addressable
- LogViewer
- 데이터 저장 불러오기, 변수 이름 Replace
- 상태 변수 저장 관리
- 유니티 설계 경험 기록
- 지도, 지도 여러종류
- 집까지 길 없게
- 타입 상성
- 메인 인형은 전직? 스타레일 개척자, 아닌 애들은 그냥 생 캐릭터

## 📀 돌

---

### ~ 2504

- VFX Graph
- UnitStatCalculator 기반

### ~ 2411

- 241111
  - 카메라 줌
  - MCamera
  - InputManager Event

### ~ 2405

- 애니메이션 텍스트 좀 더 구체화 (여러 곳에서 쓸 수 있게, 레벨업 효과)
- 포션을 섞고 삶을 바꿀 시간이군!
- UI 보여지는 시간, 특히 퀘스트
- Dotween Free
- 라이트맵 저장 문제

### ~ 2403

- 피격 시 카메라 확대, 흔들림
- 사망 시 짧은 슬로우 모션
- [사망 연출](https://twitter.com/wombatstuff/status/1659144219976511488?s=20)
- 화면 전환 연출/기능
- 스킬에 마우스 올리면 설명
- 인게임 성장 시스템 변경
  - 새로운 시스템 & UI 템플릿
- 난이도, 난이도 UI
- 피격 이펙트 (카메라 쉐이킹, 이미지)
- [TimeScale 분리](https://x.com/saewooh/status/1686563906268069888?s=20)
- 상점
- 도전과제
- 던전 진입, 던전 결과

### ~ 2401

- SOManager를 만들어 ScriptableObjects들을 관리
- 확률 새로운 기능 추가
  - List에 저장된 확률의 총량이 100보다 작을 경우, default 값을 나머지로 100을 채우는 기능
- 몬스터가 더 이상 아이템을 직접 인벤토리에 넣지 않고, EXP 오브젝트 같이 아이템 오브젝트로 드롭함
- 배경음/효과음 수정
- 슬라임
- 카메라 회전
- 카메라 기준, 특정 오브젝트가 플레이어 왼쪽에 있는지 오른쪽에 있는지 판별
- 그 외 이것저것

### ~ 2311

- 일시정지
  - 단순 ESC 메뉴
  - 어빌리티 선택 시 시간 정지
- 던전
  - 여러 몬스터 / 웨이브
  - 클리어 개념
- 데미지 텍스트 폰트 및 크기 및 위치
- 아이템 획득 팝업 크기
- 카메라
- 몬스터 스폰 범위
- 스킬 슬롯
- 던전 입장/퇴장 시 레벨, 경험치, 체력 초기화
- 던전 퇴장 시 드롭 오브젝트 비활성화
- 무적 시간
- ? 경험치 오브젝트 획득 애니메이션
- 몬스터 스폰 소환진
- ? 스테이지 가장자리에서 나오도록
- 던전 퇴장 시 스킬 오브젝트 비활성화
- 몬스터 행동트리
- 경험치 바 애니메이션
