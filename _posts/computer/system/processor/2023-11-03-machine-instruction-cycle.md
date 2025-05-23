---
title: "Machine Instruction/Cycle - 기계 명령어, 기계 사이클"
# description: ""
categories: [컴퓨터, 시스템]
tags: []
image: "/assets/img/background/kururu-lab.jpg"

date: 2023-11-03. 14:23
last_modified_at: 2024-08-29. 22:11
---

## Machine Instruction - 기계 명령어

---

- 기계 명령어 Machine Instruction
  - CPU가 처리하는 명령어 단위
    - 고급 언어로부터 번역되어 실행 시 메모리에 적재
    - CPU에 의해 인출되어 처리됨
  - 연산코드 Operation Code 와 피연산자 Operand
    - 연산 코드는 피연산자에 적영할 덧셈, 뺄셈 등의 연산을 의미하는 코드
    - 피연산자는 연산에 사용될 값을 의미
    - 피연산자로 주기억장치 주소, 상수 ,CPU 레지스터 번호 등이 가능
    - = 위와 같이 다양한 형태의 피연산자를 어드레싱 모드 ADdressing mode라 함
    - 피연산자 부분의 크기는 주기억장치의 크기에 영향을 받음
    - #전형적인 기계 명령어 포맷 연산코드 4비트+피연산자 12비트  
    - #피연산자 최대 크기에 맞춰서  

## Machine Cycle - 기계 사이클, (Instruction Cycle - 명령 사이클)

---

[참고](https://gamedevlog.tistory.com/71)  

Instruction: 명령, (사전 = 지침)  

- Fetch (=bring) 인출
  - CPU가 명령을 수행하기 위해 그 명령어를 레지스터에서 꺼내 오는 것
  - 위 말고도 그냥 일반적으로 가져온다는 뜻으로 많이 쓰이기도 하는 듯

- (CPU) 명령 사이클 Instruction Cycle (기계 사이클 Machine Cycle)  
  - CPU의 일과
    - Memory(#주기억장치)로부터 끊임없이 기계 명령어를 주소 번호대로 (차례로) 인출, 해당 명령어가 요구하는 동작을 수행/처리  
    - 점프를 의미하는 기계 명령어를 만나면 명령어 인출 위치를 변경
  - 인출 사이클 Fetch Cycle
    - 이번 차례 주소(PC가 가르키는 곳)의 주 기억장치에서 명령어를 읽어 옴
    - 인출이 완료되면, PC는 다음 차례의 명ㄴ령어 주소로 업데이트됨
  - 해독 사이클 Decoding Cycle
    - 연산 코드를 분석하여 어떤 연산인지를 식별함
  - 피연산자 사이클 Operand Cycle
    - 피연산자 인출이 필요한 경우 지정된 곳에서 피연산자를 읽어옴
  - 실행 사이클 Execution Cycle
    - 누산기와 피연산자 사이에 연산을 적용하여 명령어를 실행
  - #더 세부적으로 나눌 수도 있고, 각 단계를 더 나눌 수도 있음 (마이너 사이클 or Micro Operation != 메이저 사이클)
  - #톱니바퀴형 파이? 클럭 (CPU 파형)?

## Clock - 클럭

---

- @여치
- 클럭 CLOCK
  - CPU와 같은 전자회로는 내부적으로 동기(Sync.)가 맞아야한다.
  - 회로는 이전의 데이터값에 영향을 받아 작동하므로 이전상태를 [기억]하고 있어야하며 이전 상태와 현재 상태를 가르는 기준으로, 클럭이라 부르는 사각파 전기신호를 사용
  - 파형의 한 주기가 한 클럭, 한 주기가 바뀔때마다 새로운 상태 (개념적으로, 이전 상태와 현재 상태가 같을 수 있음)
  - 명령어는 한 클럭(한 주기)만에 완료되는 것도 있지만, 아닌것도 많다.
    - 회로구성이 이전 상태 (이전 주기)를 필요로 하는 명령
    - 메모리 칩 등 속도가 느린 장치를 억세스할때 속도를 맞추기 위해 대기
  - I.E. 2.4GHz 펜티엄 4, 2.4GHz = 클럭 주파수, 초당 24억번 클럭 주기
