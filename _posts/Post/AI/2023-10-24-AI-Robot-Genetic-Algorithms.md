---
title: "🌑 Genetic Algorithms - 유전 알고리듬"
date: 2023-10-25. 10:05
last_modified_at: 2023-10-25. 10:05
categories: ⭐Computer 🌑Computer-General
---

N차시  

@ 용불용설  
@ 루카 LUCA  
@ En~ : ~이 되게 하다  
@ Takes Place : 발생하다  

### 💫 Genetic Algorithms - 유전 알고리듬

---

계산 문제 해결에 쓰는  
Simulated Evolution 모의 진화, 진화 흉내  
를 알아본다  

유전 알고리듬  
유전자 알고리듬 (X, 잘못된 표현)  

유전 알고리듬은  
탐색 알고리듬이다  

주어진 문제를 해결하기 위한  
Encoded 암호화된 Candidate 후보 Solutions  
Population 모집단  
동작하는  
알고리듬이다  

간단한 알고리듬의  
Sequence of Instructions 명령어 열  
을 진화시키는 진화적인 계산을 통해  
유전 알고리듬의 Use를 보여준다  

Phenomenon 현상 of Natural Evolution를 흉내내는  
Optimization 최적화 알고리듬이다  

자연 진화에 있어서  
Species 종은  
복잡한 환경 속에서, 치열한 경쟁 속에서  
생존하기 위해 적응하는 방법을  
Search 탐색한다  

탐색, Chromosomes(DNS)에서 일어나는 변화와  
그 효과는  
생존과 Reproduction 재생산에 대한  
Graded 점수로 매겨진다  

Natural Selection 자연 선택  
~  

### 💫 Genetic Algorithm High-Level Flow

---

1. Initialization
   - 문제 정의
   - 인코딩 (컴퓨터가 처리할 수 있는 형태로, 자료구조 지식 요구)
   - 적합도 함수 디자인
2. Evaluation
   - 적합도 계산 (적합도 함수 사용)
3. Selection
   - 선택 연산
4. Recombination
   - Generic Operation 유전 연산
     - Crossover 교차
     - Mutation 돌연변이

사람이 관여하는 단계는  
Initialization : 문제 정의, 인코딩, 적합도 함수 디자인  

적합도 평가(계산) 단계  
I.E. PPT 라면 맛 척도 7, 10, 9, 5  

Selection 선택 단계  
모든 맛 척도를 더하고, 그 비율을 원판에 표시  
랜덤으로 선택  
비율이 낮은 요소도 꽤 높은 확률로 선택될 수 있음 = 자연선택  
좋은 것만 선택하지 않음  

Genetic Operation 유전 연산 단계  
Crossover 교차, Mutation 돌연변이  

부분 교체 (부모 유전자 섞이듯),  
돌연변이 : 아주 드물게, 부모에게 없는 성질을 주기 위해  
(교체보다 나빠질 확률이 높음, 교체보다 비율을 적게)  

@ 대부분 나빠지는 경우가 많은데,  
@ 공학적(수학적)인 문제의 경우, 모집단의 평균 점수는 높아짐  

I.E.  

재료 들어가는 경우의 수
MSG, 계란, 파, 김 = 16 - 1(아무것도 안넣는 경우) = 15  
1 = 0001, 2 = 0010, 3 = 0011, ...  
레시피 Like DNA  
레시피 번호를 통해 어떤 재료가 들어가있는 지 알 수 있음 (2진수)  

@ 실제로는 재료 종류가 많겠죠  

데이터를 기반으로 맛을 평가할 수 있는 함수 (적합도 함수)  

모집단 만들기  
임의의 모집단 요소 수 (초매개변수)  

적합도 함수 계산  

Selection 선택  
누적막대  

유전 계산  
일반적으로 모든 요소를 교차하지 않음,  
일반적으로 70% 교차?  
초매개변수  

돌연변이  
염색체 단위가 아니라 유전자 단위로  
아주 드물게  

### 💫 Sample Problem

---

숫자가 아니라 기호를 다루는 문제를 최적화하는 문제를 다뤄보자  
-> 명령어들의 열  

스택 머신  

- DUP : A -> A A, Duplicate
- SWAP : A B -> B A
- MUL : 2 3 -> 6, Multiply
- ADD : 2 3 -> 5
- OVER : A B -> B A B, 위에서 두 번째에 있는 요소 DUP
- NOP : No-Operation, Filler

I.E.  

x^8 -> DUP MUL DUP MUL DUP MUL  

DUP : x -> x x  
MUL : -> x^2  
DUP : -> x^2 x^2  
MUL : -> x^4  
DUP : -> x^4 x^4  
MUL : -> x^8  
