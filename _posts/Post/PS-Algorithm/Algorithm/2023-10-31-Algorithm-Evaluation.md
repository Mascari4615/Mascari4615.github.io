---
title: "🌓 알고리듬 성능 평가"
date: 2023-10-31. 13:37
# last_modified_at: 2023-11-14. 09:40
# last_modified_at: 2023-12-08. 11:02
# last_modified_at: 2024-02-17. 15:56
last_modified_at: 2024-02-17. 18:02
categories: ⭐Computer 🌓PS-Algorithm
tag: Algorithm Big-O
---

@ 3~5차시  

## **💫 알고리듬의 성능 평가, F Evaluation**

---

어떤 알고리듬이 더 좋냐에 대한 평가 기준은 실행 시간과 메모리 공간.  
(동일한 목적을 가지고, 결과가 정확하다는 가정하에)  

현대에 와서는 메모리가 넉넉해져서, 실행 시간을 좀 더 우선적으로 봄.  
(물론 메모리가 한정적인 임베디드는 공간도 중요)  

- 같은 문제, 다른 성능
  - 다항식 계산 : 각 항 계산 < 호너의 규칙
  - 1~n 정수 합 : for 계산 < 등차수열의 합 공식
  - 정의역 밖 요소 탐색 : 순차탐색 < 정렬된 배열에서 순차탐색 (Invalid 값에서 Early Return) < 이진탐색

- 실행 시간 측정의 문제점
  - 컴퓨터 스펙에 따라
  - 언어, 컴파일러, 프로그래밍 스타일 및 코딩 표준에 따라
  - 실행할 때마다 실행 시간이 달라질 수 있음
  - 가능한 모든 입력에 대해, 정확한 결과(!근사)를 출력하도록 `완성`해야

실행 시간 측정은 알고리듬 자체의 성능 이외의, 외부 영향을 많이 받는다.  
→ 복잡도 분석  

어림잡아 3~5억 번의 연산/1초  
어떤 연산을 하는지에 따라  
단순한 연산 : 비트 AND, OR, 비교, 덧셈  
복잡한 연산 : 곱셈, 나눗셈, 대입, 함수 호출  

2000만?  

보통 문제에서 1~5초 정도가 주어진다  
-> 입력 범위를 보고 문제에서 요구하는 시간복잡도를 유추  

<br>

<!-- ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ---- -->

## **💫 복잡도 분석**

---

계산이나 추론 등을 통하여 알고리듬을 실행하는데 필요한 양을 결정하는 작업  
(시간 복잡도, 공간 복잡도 = 실행 시간, 메모리 공간)  

현실적으로, 측정 없이 불가능한데, 측정은 외부 영향을 많이 받음  
현실적인 대안으로, 실행시간을 가늠할 수 있는 `간접적 지표`을 계산하여 시간 복잡도의 기준으로  

시간 복잡도  
입력의 크기와 문제를 해결하는데 걸리는 시간의 상관관계  

- 시간 복잡도의 기준
  - 연산 실행 횟수
    - 연산 실행 회수는 n에 대한 함수 꼴 T(n) = 그래프
      - 최댓값 찾기 : 탐색 대상 숫자의 수에 따라
      - 행렬 곱 : 행렬의 행과 열의 값에 따라
      - 정렬 : 정렬 대상 원소의 수에 따라
  - 명령문 실행 횟수
    - 큰 알고리듬에서 연산 실행 횟수 계산 어려움
  - 기준연산 실행 횟수
    - 기준연산 : 실행 시간의 계산에 있어서 영향을 가장 많이 주는 연산
    - 기준연산이 명확하지 않으면 어려움

N이하의 수 중에서 가장 큰 2의 거듭제곱수를 반환하는 함수 (N은 10억 이하의 자연수)  
로그의 정의에 입각해서 k = LogN, O(LogN)

@ U 중간고사 출제 : 버블 정렬, 기준연산 기준 실행횟수를 구하시오. (n = 101, 등차등비)  

점근 분석, Asymptotic Analysis  
= 복잡도 함수를 '단순한' 근사 함수(무한으로 가면 비슷한 꼴)로  
→ 최고 차항을 계수를 1로 하여 추출  

계수, 나머지 항 생략해도 되나?  
→ 무한으로 갈수록, 식에서 최고 차항 비율은 겁나 커진다  
→ 무한으로 갈수록, 계수 \< 지수  

복잡도 등급 - 입력 크기(n) 비례 복잡도(결과, 처리시간) 증가  
→ 상수, 로그, 선형, 선형로그, n차, 지수, 팩토리얼, ...  

@ 정렬 - 선형로그  
@ 제곱 - 행렬 합  
@ 세제곱 - 행렬 곱  

@ msps - 초당 백만번 연산  
@ 단순 연산(비트 연산 등)과 상대적 복잡 연산과의 괴리  
@ flops - 초당 부동소수점 연산  

공간 복잡도 (Space Complexity)  
입력의 크기와 문제를 해결하는데 필요한 공간의 상관관계  

512MB = 1.2억개의 int  
기억하면 좋다  

int 1개가 4바이트라는 걸로 기억  
예를 들어 크기가 5억인 배열이 필요하다 -> 틀린 풀이니까 다른 풀이를 고민  

<br>

<!-- ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ---- -->

## **💫 점근 표기법**

---

@ U 중간고사 출제 : (두 가지 경우에 대해서만 n^2, 다른 모든 경우에 대해서는 n * log n 시간복잡도를 가지는 알고리듬에 대해) Big O, Big Θ, 최악의 경우 의미  
-> '최악의 경우'가 붙으면 세타가 더 적절하다 O도 틀린 건 아니지만..  
-> 최악의 경우 세타와 그냥O는 같은 뜻인가? X  

Big O, Big Θ, Big Ω  
@ 소문자와 구별되기에, Big 붙여야  

### **🫧 Big O, 점근적 상한**

아무리 많아도 이정도 걸린다  

I.E.  
→ T(n) = 2x + 4 일때, O(3x)  
→ 5n^2 + 3n - 10 = O(n^3)  
→ 5n^2 + 3n - 10 = O(n^2)  
→ 5n^2 + 3n - 10 != O(n)  

When  
→ 입력 데이터에 따라 증가율이 달라지는 경우  
→ 정확한 복잡도는 모르고, 상한은 아는 경우  
→ 관례적 (그냥 많이 써서)  

상한의 불확실성 (빡빡한 상한, 느슨한 상한)  
→ 정의를 만족하는 가장 낮은 차수를 사용하는 것이 원칙  

@ =은 equal, is가 아니라 포함되어 있다 라는 의미  

### **🫧 Big Ω, 점근적 하한**

최소한 이정도 걸린다  

I.E.  
→ T(n) = 2x + 4 일때, Ω(n)  

When  
→ 입력 데이터에 따라 증가율이 달라지는 경우  
→ 정확한 복잡도는 모르고, 하한은 아는 경우  
→ 다른 점근 표기법 보완 (보통 혼자 쓰지 않음)  

f(n) = O(g(n)) \<=> g(n) = Ω(f(n))  

### **🫧 Big Θ, 점근적 상한과 하한이 일치**

대략 이정도다  

I.E.  
→ T(n) = 2x + 4 일때, Θ(n)  

When  
→ 정학한 복잡도 함수를 아는 경우  

### **🫧 BlaBla**

복잡도 - O, Ω  
(~한 경우) 복잡도 - Θ  

동일한 기능의 알고리즘 비교  
A = O(n^2), B = O(n^3)  

A가 B보다 빠르다 X  
A가 B보다 점근적으로 빠르다 O  

n의 값이 고려되어야 한다  
I.E. A = 10^5 * n^2, B = n^3, n \< 10^5 라면 A < B  
n이 작으면 시간 차이 별로 없거나, 오히려 점근 복잡도가 낮은 알고리즘이 더 느릴 수 있다  

점근 복잡도는 수학과 공학의 절묘한 균형을 요구  
@ TODO : 공학 ?  

점근 복잡도 쉽게 구하기  

1. n에 따라, 순차적인 명령문(블록)은 점근 복잡도 함수를 더한다
2. n에 따라, 중첩된 명령문(블록)은 점근 복잡도 함수를 곱한다
3. 부프로그램(함수)도 점근 복잡도를 반영

최악, 최선, 평균 복잡도  

n 같더라도 집합-순서에 따라 실행 시간 달라지는 알고리즘  
Big O 점근석 상한 만을 나타내기도  

최선 \<= 평균 \<= 최악 복잡도  
최악과 최선 복잡도가 같다면, 평균적인 경우도 같고, 이는 Θ 표기법으로  

평균 복잡도  
최악에 가까운, 버블 정렬, 삽입 정렬  
최선에 가까운, 퀵 정렬  

의미 차이  

최악의 경우 Θ(n^2)  
→ 최악의 경우 n^2가 걸린다  
최악의 경우 O(n^2)  
→ 최악의 경우, 정확하게는 모르겠지만 그 상한이 n^2이다  

최악의 경우, 최선의 경우, 평균적인 경우 Θ(~)  
== O(~), Ω(~)  

<br>

<!-- ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ---- -->

## **💫 Big O Notation**

---

코테에서는 빅오 표기법만 보면 된다.  

알고리즘이 얼마나 빠른지 표시하는 특별한 방법  
주어진 식을 값이 가장 큰 대표항만 남겨서 나타내는 방법.  

i.e. n개의 원소, 단순 탐색은 n번 연산, O(n)  
초 같은 시간 단위는 어디로? 빅오 표기법은 속도를 시간 단위로 세지 않음  
연산 횟수를 비교하기 위한 것  

### **🫧 주의 : 알고리듬간 속도 비교 시**

100개의 원소, 단순 100번, 이진 7번  
이진 탐색은 단순 탐색보다 15배 빠른 알고리듬이다? XXX  

10억개의 원소, 단순 10억번, 이친 32번  
이 경우에는 이진 탐색이 단순 탐색보다 3천3백만배 빠르다  

리스트의 크기에 따라 실행 시간이 증가하는 비율이 다르다  

-> 알고리듬의 실행시간이 얼마나 걸리는지만 고려할 것이 아니라  
-> 리스트의 크기가 증가할 때 어떻게 증가하는지를 파악할 필요가 있다  

### **🫧 주의 : Big O는 최악의 경우에 대한 것**

i.e. 단순 탐색, 사전에서 a를 한 번에 찾았으므로 O(1)? XXX  

빅오는 **최악의 경우**에 대한 것  
절대로 ~보다는 느려지지 않는다는 사실에 대한 보장  

### **🫧 빅 오 실행시간의 예**

- O(1) : 상수 시간
  - 5, 16, 36
- O(LogN) 로그 시간 Logarithmic Time
  - 이진탐색
- O(N) 선형 시간 Linear Time (데이터 크기와 실행 횟수가 똑같은)
  - 5N + 3, 2N + 10LogN, 10N
  - 단순탐색
- O(NLogN) 다항 시간
  - NLogN + 30N + 10, 5NLogN + 6
  - 퀵 정렬 같이 빠른 정렬 알고리듬
- O(N<sup>2</sup>) 다항 시간
  - N<sup>2</sup> + 2N + 4, 6N<sup>2</sup> + 20N + 10LogN
  - 선택 정렬과 같이 느린 정렬 알고리듬
- O(2<sup>N</sup>) 지수 시간
- O(N!)
  - 12!은 약 5억
  - 외판원(세일즈맨) 문제와 같이 정말 느린 알고리듬
    - Traveling Salesperson Problem
    - 모든 도시는 가장 짧은 거리의(시간의) 경로
    - 아직 이것보다 빠른 알고리듬이 알려지지 않음
    - 대략적인 답을 얻는 것 밖에 (이진 탐색 트리)

| N의 크기 | 허용 시간 복잡도 |
| N <= 11 | O(N!) |
| N <= 25 | O(2<sup>n</sup>) |
| N <= 100 | O(N<sup>4</sup>) |
| N <= 500 | O(N<sup>3</sup>) |
| N <= 3,000 | O(N<sup>2</sup>LogN) |
| N <= 5,000 | O(N<sup>2</sup>) |
| N <= 1,000,000 | O(NLogN) |
| N <= 10,000,000 | O(N) |
| 그 이상 | O(LogN), O(1) |

절대적인 기준은 아니다 (느낌만)  

### **로그**

log<sub>10</sub>100이라는 수는 "10을몇 번 곱해야 100이 될까?" 하고 묻고 있는 것  
10 * 10 = 100 이니까 답은 2  
그러니까 log<sub>10</sub>100 = 2  
즉, 로그는 거듭제곱의 반대말  

빅오 표기법에서 모든 log 함수는 log<sub>2</sub>를 뜻한다  

### **🫧 요약**

- 알고리듬의 속도는 **시간**이 아니라 연산 횟수가 **어떻게 증가하는지**로 측정
- 입력 데이터의 크기가 늘어날 때 알고리듬의 실행속도가 얼마나 증가하는지 알 수 있다
- 알고리듬의 실행시간은 빅 오 표기법
- O(log n)은 O(n)보다 빠르고, 찾으려는 리스트의 원소의 개수가 증가하면 상대적으로 더 빨라진다.