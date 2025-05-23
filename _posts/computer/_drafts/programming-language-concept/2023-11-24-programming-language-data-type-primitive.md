---
title: "프로그래밍 언어 - Primitive Data Type"
# description: ""
categories: [컴퓨터, 🌒Programming]
tags: [Data-Type]
image: "/assets/img/background/kururu-lab.jpg"

date: 2023-11-24. 09:20
# last_modified_at: 2023-12-01. 10:20
# last_modified_at: 2023-12-08. 08:58
last_modified_at: 2023-12-15. 08:42
---

## 기본 데이터 타입 - Primitive Data Type

---

@ U 기말고사 출제: 언어가 제공하는 기본 데이터 타입에 대하여 설명하시오.  

- 기본 데이터 타입은 프로그래밍 언어에서 기본적으로 제공되는, 또한 다른 타입으로 정의되지 않는 타입을 말한다.
- 기본 데이터 타입은 구조화된 데이터 타입(배열, 구조체 등)을 제공하기 위해 활용된다.

- 하드웨어 반영 기본 데이터 타입: 정수(int), 실수(float)
- 약간의 비하드웨어적 지원을 받는 기본 데이터 타입도 있을 수 있음

## 수치 타입

---

- 초기부터 오늘날까지 프로그래밍 언어에서 수치 타입은 기본적으로 제공되고 있다.

### 정수

- 현대의 컴퓨터는 다양한 크기의 정수 타입을 지원하고 프로그래밍 언어 또한 이를 반영하여 지원
  - Java 부호화 정수: byte, short, int, long
  - C/C++ 부호화/비부호화 정수: int, unsigned int, short, unsigned short, ...
  - Python: 길이에 제약이 없는 정수 타입
    - 하드웨어에 의해 직접 지원되지 않는 정수 타입 (비하드웨어적 지원을 받는 정수 타입)

- 음의 정수 표현
  - 부호-크기 표기법
    - 부호 비트가 0이면 양수, 1이면 음수
    - 크기는 절대값을 표현
    - 문제점: 산술 연산을 위한 컴퓨터 하드웨어 제작이 매우 어렵다
  - 2의 보수 표기법
    - 음수를 표현하는데 2의 보수 표기법 사용
    - 산술 연산을 위한 컴퓨터 하드웨어 제작이 아주 쉽다
    - 1의 보수를 만든 후 1을 더해줘서 2의 보수를 쉽게 생성 가능

### 부동 소수점

- 실수 값, 하지만 대부분 실수 값에 대한 근사값
- 산술연산 시에 정확도를 상실한다는 문제점
- 과거에는 컴퓨터마다 부동 소수점을 표현하는 방식이 달랐으나, IEEE에서 부동 소수점 표현을 표준화 함 -> IEEE 754
  - 단정도(Single precision) -> float, 배정도(Double precision) -> double

@ PIC 0001, 0002  

### 고정 소수점, 십진수

@ PIC 0003  

- 십진수 데이터 타입은 고정된 수의 십진수 데이터를 저장, 소수점은 고정된 위치를 가짐

- 제한된 범위에 포함된 십진수 값들을 정확하게 저장 할 수 있음
  - 사무용 데이터 처리를 위한 기본적인 데이터 타입

- 컴퓨터의 십진수 표현(BCD: Binary Coded Decimal) 지원 여부
  - 사무 시스템 응용 분야를 지원하기 위해 설계된 큰 규모의 대부분의 컴퓨터에서 십진수 데이터 타입을 위한 하드웨어 지원을 포함
  - Intel CPU의 경우 제한적 지원
  - 하드웨어적으로 BCD처리가 지원되는 경우 하드웨어적으로 처리, 그렇지 않으면 소프트웨어 적으로 처리(에뮬레이팅) 함

```cs
double doubleTemp = 0.1 + 0.2;
Console.WriteLine(doubleTemp == 0.3); // false

decimal decimalTemp = 0.1m + 0.2m;
Console.WriteLine(decimalTemp == 0.3m); // true
```

### 불리안 타입

- 참과 거짓을 표현하는 가장 단순한 타입

- 스위치나 플래그를 표현하는데 사용
  - 정수와 같은 타른 타입이 이런 목적으로 사용될 수 있지만 가독성 측면에서, 불리안 타입 사용

- 한 비트로 구현이 가능하나 컴퓨터에서의 최소한의 접근 단위 때문에 한 바이트로 구현

- 수치식이 조건식으로 허용되는 언어도 있고, 안되는 언어도 있고
  - 0 false, 1 true

### 복소수

- Python: 복소수와 복소수 연산을 지원, 허수부는 j 혹은 J로 표현

```py
>>> (5 + 2j) + (7 + 2j)
(12 + 4j)
>>> (5 + 2j) * (7 + 2j)
(31 + 24j)
```

### 문자

- 단일 문자 데이터. 문자 데이터는 수치 코딩으로 컴퓨터에 저장
- ASCII, ISO 8859-1, Unicode, ...

### 문자열

...  

## 문자열 - Char String

---

- 일련의 문자들로 구성되는 타입

- 문자열 상수는 출력에 레이블을 부여하기 위해 사용되며, 모든 유형의 데이터인 입력과 출력은 흔히 문자열 관점에서 이루어짐

- 설계 고려사항
  - 문자열이 단순히 문자 배열의 특수한 유형인가 혹은 기본 타입인가?
  - 문자열이 정적 길이 혹은 동적 길이를 갖는가?

### 문자열과 연산

- 가장 공통적인 연산: 배정, 접합, 부분 문자열 참조, 비교, 패턴 매칭, ...

- 배정, 비교의 고려사항: 길이가 다른 문자열간 배정과 비교는 어떻게 처리할 것인가?

- 부분 문자열 참조(Substring reference)
  - 주어진 문자열의 부분 문자열에 대한 참조 -> 슬라이스(Slices)

- in c/cpp
  - char 배열로 문자열 저장
    - 반드시 문자 '\0'으로 끝나야 함
    - 길이 정보를 따로 저장하지 않고, '\0'로 끝을 표시
    - 문자열 리터럴의 경우, 컴파일러가 자동으로 '\0'을 첨가
      - i.e. char str[] = "apples";
  - 표준라이브러리를 통해 문자열 연산을 제공
    - 문자열 연산 함수는 '\0'을 만날때까지 해당 연산을 수행
      - strcpy, strcat, strcmp, strlen

```cpp
char temp[4] = ['T', 'e', 'm', 'p'];
char temp[5] = ['T', 'e', 'm', 'p', '\0'];
char temp[5] = "Temp"; // 컴파일러가 끝에 \0 추가

// Data 영역에 ReadOnly로 "Temp"가 저장되고
// Stack에서 temp 변수가 "Temp"를 가리킴
char* temp = "Temp"; // 변수 크기: 주소 크기
char temp[] = "Temp"; // 변수 크기: 문자 수 만큼

// Heap, malloc으로 만들기

char a[10];
char b[6] = "Hello";
char c = "Hello World";
strcpy(a, c);
printf("%s\n", b); // "d" 출력
```

- C
  - 표준라이브러리의 문자열 조작 함수가 안전하지 않음
  - 목적지 문자열에서 오버플로우가 발생하는 것을 보호하지 않음
  - i.e. strcpy(dest, src): src가 dest보다 길이가 긴경우 오버플로우가 발생
- C++
  - 표준 클래스 라이브러리를 통해서 문자열(string) 지원
  - C 문자열 라이브러리의 불안정성을 보완하기위해 가급적 string을 사용 권고
- Python, JS, Ruby, ...
  - 문자열을 기본 타입으로 제공하며 Immutable

### 문자열 길이 선택사항

- 정적 길이 문자열
  - 문자열 길이는 정적이고 문자열이 생성될 때 설정
    - C++ string 타입

- 제한된 동적 길이 문자열
  - 변수 정의에 선언되고 고정된 최대 길이까지의 가변적인 길이를 갖는 것을 허용
    - C 문자열, C++에서의 C 스타일 문자열

- 동적 길이 문자열
  - 문자열이 최대 길이 제한없이 가변길이를 갖는 것을 허용
    - 동적 기억장소의 할당과 해제로 성능에 부담이 있으나 최고의 유연성을 제공
    - 웹 데이터는 대부분 문자열이다 보니 많이 쓰여서

### 평가

- 문자열 타입은 언어의 작성력에 중요한 영향을 미침

- C 스타일의 문자열 지원 방식의 부자연스러움
  - C에서는 문자열이 기본 데이터 타입이 아니고 문자 배열로 처리
    - 만약 strcpy가 제공되지 않는다면 문자열의 단순 배정도 루프를 사용해야 함

- 문자열을 기본 타입에 포함시키는 것의 비용이 많지 않음
  - 따라서 오늘날 대부분의 언어에서 문자열을 기본 데이터타입으로 포함
  - 단순 문자열 비교나 문자열 접합 연산이 기본 제공

### 문자열 타입의 구현

- 문자열 타입을 하드웨어로 직접 지원할 수 있지만 대부분 문자열 기억공간, 검색, 조작을 구현하기 위해 소프트웨어적으로 접근
- 문자열이 문자 배열로 표현될 때 (C의 경우) 언어에서 문자열 연산을 거의 제공하지 않음 -> 라이브러리로 제공

## 레코드 타입

---

@ U 기말고사 출제: 레코드 타입에 대하여 설명하고 그 의의를 설명하시오.  

- 각 요소들이 이름으로 식별
- 구조의 시작부터 오프셋을 통해 접근
  - 개개의 원소들이 동일한 타입이나 크기가 아닌 데이터의 모임을 모델링 할 때 빈번하게 사용

@ ? Java 구조체 따로 없는데?  
@ TODO: Java 메모리 구조  
  class loading (code + data)  
  stack  
  heap (managed by JVM GC)  

### 평가_레코드 타입

설계는 간단하며 사용은 안전하다.  

- vs 배열
  - 레코드는 이질적인 데이터를 허용
  - 레코드의 요소는 필드로 접근 (색인 X)
  - 순서를 고려할 필요가 없음

## 튜플

---

- 레코드 타입과 비슷하나 요소들을 이름으로 명명하지는 않음
  - 레코드 타입처럼 요소들이 이질적인 타입으로 구성 가능
- Python은 immutable한 튜플 타입을 기본 데이터 타입으로 제공
  - 이질적인 요소를 허용하며 요소에 접근시에는 첨자로 접근
- 튜플은 함수가 여러개의 값을 반환하는 것을 허용하기 위해

@ TODO: Python 괄호 종류에 따른 컨테이너 종류  

## 리스트

---

- C#, Java : 표준라이브러리, List, ArrayList

- Python: 기본 데이터 타입
  - \[ \] 대괄호
  - mutable (튜플은 immutable)
  - 요소 삭제 del temp[1]

- Python List Comprehension
  - 리스트를 생성하기 위한 매커니즘으로 집합 표기법에 기반
    - [식 for 요소 in 배열 if 조건]
    - i.e. [x * x for x in range(12) if x % 3 == 0]
  - 슬라이스 연산도 제공

## 공용체(Union) 타입

---

```c
union FlexType
{
    int intE1;
    float floatE1;
};

union FlexType el1;
float x;

// ...

eli.intE1 = 27;
x = eli.floatE1;
```

- C/C++는 타입 검사에 대한 언어 지원이 없는 자유 공용체 구조를 제공
  - C/C++에서 union 키워드는 union 구조체를 명세하는데 사용
  - i.e. el1.floatE1을 x에 배정, 이때 타입 검사를 하지 않음
  - 왜 쓰냐? Low-level 시스템 프로그래밍에 공용체를 사용 (임베디드 시스템/네트워크)

- 변수가 프로그램 실행 중에 다른 시기에 다른 타입의 값을 저장할 수 있는 타입
- 설계 고려사항
  - 타입 검사가 요구되는가?
  - 공용체가 레코드에 포함될 수 있는가?
- 판별 공용체와 자유 공용체
  - 자유 공용체: 타입 검사에 대한 언어 지원이 없는 형태의 공용체: C/C++
  - 판별 공용체: 공용체 구조에 타입 지시자(판별자)가 포함되어있어서 이를 이용하여 타입 검사를 수행하는 공용체

- 평가
  - 강타입 언어가 아닌 경우, 공용체는 안전성에 문제가 생길 수 있음
    - C/C++ 은 강타입 아님
    - Java/C#은 공용체가 없음

- vs 구조체
  - 구조체와 같은 문법
  - 구조체는 각 요소가 각자의 메모리 공간을 가짐
  - 공용체는 모든 요소가 하나의 메모리 공간을 공유
    - 요소들 중 가장 큰 요소 크기 만한 메모리 공간
  - 공유하는 똑같은 메모리 공간을 어떤 타입으로 접근하냐 - 어떤 모드로 접근할거냐

- 왜 씀?
  - 메모리 절약
  - 현대에는 메모리 널널해져서 구조체 쓰기 공용체는 잘 안쓰는 듯?
