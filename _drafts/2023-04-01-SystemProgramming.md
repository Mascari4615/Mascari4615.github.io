---
title: "🌱 시스템 프로그래밍"
date: 1999-01-01. 00:00
categories: 🪨Stone 🌱DayStone
---

- 배우는 것
  - 컴퓨터 작동 방식과 기본적 구성
  - 좋은 프로그래밍을 위한 성능 분석 방법
  - 최신 프로세서 (캐시, 파이프라인)에 영향을 미치는 문제

- 배우는 이유
  - 컴퓨터 과학자
  - 성능 좋은 SW
  - HW 구매 결정, 전문자로서 조언 제공

- 교과 내용
  - 컴퓨터 시스템의 전반적 개념
  - 프로그램 구조와 실행
  - 시스템에서 프로그램 실행 원리
  - 프로그램의 상호작용 및 통신

- 1.1 Info = Bit + Context

- 1.2 Compile System
  - 목적 프로그램
    - 재배치 가능 목적 프로그램 -> 목적 파일
    - 실행 가능 목적 파일 -> 실행 파일
  - Unix 컴파일
    - gcc -o hello hello.c
    - @ GNU
      - @ Free SW : "free" as in "free speech", not "free beer"

- 1.3 Understanding of Compile System
  - Program Performance Optimization
    - Understanding of LLL
    - switch vs if-else, while vs for
  - Understanding of Linking Error
    - Link-Time Error, Compile-Time Error
  - Avoiding Security Holes
    - Buffer Overflow Bugs
    - Security Holes on the Internet and Networks

- 1.4 ComputerSystem-HW Configuration @
  - CPU
    - CPU operations
    - Load - Operate - Store - Jump
  - The process of Loading "hello" Code from KeyBoard... @
  - The process of Loading Executable File From Disk To MainMemory... @



gcc -o temp.c 실행 가능 목적 파일 (실행파일, object, 링크까지 끝난)  
gcc -c temp.c 재배치 가능 목적 파일 (목적파일, 링크는 없는 그냥 목적 파일)  

Concurrent Process 병렬 프로세스  

어셈블리 특성 : 연산

레지스터나 메모리 데이터로 산술함수 수행  
ALU에서 연산을 하려면 데이터 필요  
레지스터에 있으면 레지스터에서
메모리 데이터에 있으면 메모리 데이터에서 데이터를 읽어 산술함수 수행

메모리와 레지스터 사이에 데이터 전송 (버스를 통해)

- Memory to CPU, 메모리에서 레지스터로 데이터 전송 (Load)
- CPU to Memory, 레지스터 데이터를 메모리에 저장 (Store)

전송 제어 (Transfer control)

- 프로시저까지 또는 프로시저에서 무조건 점프, 무조건 분기 like goto (to/from procedures)
- 조건 분기 if else (conditional branch)

요즘 프로그래밍 언어
스트럭쳐드 프로그래밍  
goto가 없음

근데 어셈블리는 있다

---

목적 코드 생성

Linux, gcc -Og -c sum.c

-c 옵션  

as에 의한 어셈블까지만 수행  
링크는 미수행  

sum.o 파일 산출  

14바이트 안에 sum의 목적코드 내장 (해보니까 14바이트라는 뜻)  

-Og
최적화 명령어

---

목적코드

슬라이드 참고 - Code for sumstore, 이전에 봤던 어셈블리 코드를 머신코드로 바꾼 것  
시작 어드레스부터 1++ 바이트만큼 떨어진 위치에 각각 코드가 위치한다  

어셈블러 (Assembler)  
.s를 .o로 번역  
명령어 각각을 이진 인코딩  
거의 완벽한 실행 코드  
다른 파일들과의 코드 연결 (linkages)은 빠짐  

링커 (Linker)  
파일들 사이의 참조를 해결  
정적 런타임 라이브러리와 조합 (i.e. code for malloc, printf)  
일부 라이브러리들은 동적으로 연결 (Dynamically Linked), 프로그램 실행 시 링킹 발생  

---

sso
인증 관련한
바디 페이로드 차이??
메시지 타입을 정의할 ㄸ ㅐ바이트 혹은 비트 단위로 필드를 다눠서 할 수도 잇고
HTTP는 요처아이낳고 헤더부분하고 가 다르게 들어가잖아요?
문자열 스페이스두고 URL 들어가고 버전 메소드 URL ㅣㅇ런식으로
무튼 2가지 방법이 있다
비트/바이트 방법
텍스트 방법 (http)
대부분은 http처럼 텍스트 기반으로 만들고 있따
경랑 디렉터리 접근 프로토롤
LDAP
전화번호부 책
LDAP은 전화번호부라고 보면된다
네트워크에 자원이 많이 있을텐데 이를 효율적으로 관리하기 위한
표준으로도 나옴
전기 통신 (전화와 관련된) 글너 표준을 만든 단체 ITU에서 만든 표준잉 X.500
X.500 을 기바느올 만들어진프포토콜인 LDAP
FIND PRINT 여러가지 하드웨어 리소스들이 있을 텐데 어떻게 관리할것인지
개별적인 자원 식별자 들 (이름 부여)하고 그담에 그런 개별 자원에 접근할 때 어떤 권한을 가지고 접그낳ㄹ ㅜㅅ있는지
그런 자우너을 관리하는 관리자가 있다면 그러ㅁㄴ 관리자 ~ 까지 할 수 ㅣㅇ씩 헺는
MS에서도 OpenLDAP 마늠
윈도우에도 잇으ㅁ
무튼 파일 식별하려면 이름이 잇어야하잖아요
DNS처ㄻ 계층적으로 이름 공간을 구성해서 사용
엔트리가 개별 자원 = 고유 식별 이름
노드 별로 
노드에 할당된
ㄴ드를 연결해서
고유한 이름을 만들게 되는데
보게 되ㅣ면
dc = 도메인 컴포넌트
ou = 조직 단위
dn =
LDAP URL 다음시간에 설명할텐데
일반적으로 사용할 일은 없다
구체적인 내용은 기억하지 않아도되지만
LDAP이 마치 자원을 전화번호부처럼 써서 효율적으로 쓰기위한 프로토콜이다
라고 생각
원격 제어
팀 뷰어 같은
원격이 떨어져있는 사람의 컴을 제어하기 위한
원격 제어 그냥 이런 기능이 있따 정도로 기억

---

*dest = t;  
movq %rax, (%rbs)  
0x40059e: 48 89 03  

C Code  
dest가 지정한 곳에 값 t를 저장  

Assembly Code  
> 8 바이트 값을 메모리로 이동  
>> x86-64 용어로 Quad words  
> Operands
>> t: 레지스터 %rax
>> dest: 레지스터 %rbx
>> *dest: 메모리 M[%rbx]

r = register  

Object Code  
> 3 바이트 명령
> 주소 0x40059e에 저장됨

(범용 레지스터)  
64bit 16개  
32bit 8개  

실행 가능 파일 생성  
실행파일 생성하려면 링커 필요  
One object file must contain main  
Combines with static run-time livraries (e.g., printf)  
Some libraries are dynamically linked (i.e. at execution)  

Obtain with command C code  
gcc -Og -o prog main.c sum.c  

목적코드의 역 어셈블  
Disassembled  

Disassembler  
objdump -d sum.o  
목적코드 조사에 유용한 도구  
일련의 명령들 비트 패턴을 분석  
어셈블리 코드와 유사한 해석 산출  
a.out(complete executable) 이나 .o파일을 실행할 수 있음  

역어셈블의 다른 방법  
Within gdb Debugger  
gdb sumstore  
disassemble sumstore  
Disassemble procedure  
x/14xb sumstore  
Examine the 14 bytes starting at sumstore  

역어셈블 할 수 있는 것은?  
실행코드로 번역될 수 있는 것  
역어셈블리는 바이트를 조사하고 어셈블리 소스를 재구성  

드라이브보면 Programs File, Programs File (x86) 두 개  
64bit 운영체제에서 32bit도 돌아감  호환성  

C 대부분 32bit 컴파일러  

32bit 에서는 %r-- 가 아니라 %e--  

Reverse  engineeering forbidden by MS End User License Agrement  

데이터 형식  

"word" :  
인텔에서 16비트 데이터 형식 ("word" 의 기원)  
32bit : double word  
64bit : quad words  

GAS (GNU 어셈블러)에서 "/"을 붙이는 데 문제 없음  
FP도 "/"을 붙임  
왜냐하면, FP(부동소수점)는 정수와 다른 연산과 레지스터를 가짐  *dest = t;  
movq %rax, (%rbs)  
0x40059e: 48 89 03  

C Code  
dest가 지정한 곳에 값 t를 저장  

Assembly Code  
> 8 바이트 값을 메모리로 이동  
>> x86-64 용어로 Quad words  
> Operands
>> t: 레지스터 %rax
>> dest: 레지스터 %rbx
>> *dest: 메모리 M[%rbx]

r = register  

Object Code  
> 3 바이트 명령
> 주소 0x40059e에 저장됨

(범용 레지스터)  
64bit 16개  
32bit 8개  

실행 가능 파일 생성  
실행파일 생성하려면 링커 필요  
One object file must contain main  
Combines with static run-time livraries (e.g., printf)  
Some libraries are dynamically linked (i.e. at execution)  

Obtain with command C code  
gcc -Og -o prog main.c sum.c  

목적코드의 역 어셈블  
Disassembled  

Disassembler  
objdump -d sum.o  
목적코드 조사에 유용한 도구  
일련의 명령들 비트 패턴을 분석  
어셈블리 코드와 유사한 해석 산출  
a.out(complete executable) 이나 .o파일을 실행할 수 있음  

역어셈블의 다른 방법  
Within gdb Debugger  
gdb sumstore  
disassemble sumstore  
Disassemble procedure  
x/14xb sumstore  
Examine the 14 bytes starting at sumstore  

역어셈블 할 수 있는 것은?  
실행코드로 번역될 수 있는 것  
역어셈블리는 바이트를 조사하고 어셈블리 소스를 재구성  

드라이브보면 Programs File, Programs File (x86) 두 개  
64bit 운영체제에서 32bit도 돌아감  호환성  

C 대부분 32bit 컴파일러  

32bit 에서는 %r-- 가 아니라 %e--  

Reverse  engineeering forbidden by MS End User License Agrement  

데이터 형식  

"word" :  
인텔에서 16비트 데이터 형식 ("word" 의 기원)  
32bit : double word  
64bit : quad words  

GAS (GNU 어셈블러)에서 "/"을 붙이는 데 문제 없음  
FP도 "/"을 붙임  
왜냐하면, FP(부동소수점)는 정수와 다른 연산과 레지스터를 가짐  

---

간단한 메모리 주소 모드

1. 참고
   - Reg[R] : 레지스터 R 안의 값
   - Mem[M] : 메모리 M 안의 값값

2. 표준모드 (R)
   - Mem[Reg[R]]
   - 레지스터 R은 메모리의 주소를 나타냄
   - C의 포인터 역참조 (Dereferencing)
   - movq (%rcx), %rax

3. 변위모드 D(R)
   - Mem[Reg[R]+D]
   - 레지스터 R은 메모리 구역의 시작 주소를 나타냄
   - 상수 변위 D는 오프셋을 나타냄
   - movq 8(%rbp), %rdx

오퍼랜드 형태
