---
title: "DP | Dynamic Programming | 동적 프로그래밍, 동적 계획법"
# description: ""
categories: [💫Computer, 🌑Algorithm]
tags: [Algorithm, Dynamic-Programming]
image: "/assets/img/background/kururu-lab.jpg"

date: 2023-10-31. 14:16
# last_modified_at: 2023-11-16. 10:34
# last_modified_at: 2023-11-21. 13:52
# last_modified_at: 2023-11-28. 13:36
# last_modified_at: 2023-11-30. 10:30
# last_modified_at: 2023-12-05. 15:54
# last_modified_at: 2023-12-19. 01:09
# last_modified_at: 2024-03-22. 00:59
# last_modified_at: 2024-06-12. 02:57
# last_modified_at: 2024-08-29. 21:34
# last_modified_at: 2024-10-22. 14:21 # 정리
last_modified_at: 2024-11-13. 03:31 # 정리
---

{% include embed/youtube.html id = "5leTtB3PQu0" %}

## 💫 기록

---

- [DP](https://namu.wiki/w/%EB%8F%99%EC%A0%81%20%EA%B3%84%ED%9A%8D%EB%B2%95)
- [DP의 기본에 대해서...](https://stonejjun.tistory.com/23)

## 💫 Dynamic Programming | 동적 프로그래밍, 동적 계획법

---

기억하고 풀기.  
무엇을? 부문제로 나누어 푼 결과를.  

아무튼 일단 부분제를 먼저 풀어놓고 본다. 이게 해답을 구할때 쓰일지 안쓰일지는 모름.  

나중에 만약 똑같은 부문제의 답이 필요하면, 그때 저장된 해답을 이용.  
그렇게 결과를 차곡차곡 쌓아올려서 문제를 해결.  

= 문제를 해결하기 위한 점화식을 찾아낸 후, 점화식의 항을 밑에서부터 차례로 구해나가서, 답을 알아내는 형태의 알고리듬.  

## 💫 How

---

1. 테이블 정의
2. 점화식 찾은 후
3. 초기 값 설정

### 🫧 DP의 적용

1. 최적화 문제의 경우 최적 부분구조를 갖는지 검증
2. 문제를 순환적으로 정의
3. 중첩된 부문제 특성을 갖는지 조사
4. 부문제의 해답을 저장하고 이로부터 최적해를 구성하는 알고리즘을 구축

## 💫 Use

---

- [LIS \| 최장 증가 부분 수열](/posts/algorithm-lis/)
- [LCS \| 최장 공통 부분 수열/순서](/posts/algorithm-lcs/)

- [Fibonacci](/posts/algorithm-fibonacci/)
- [0-1-KnapSack-Problem](/posts/0-1-knapsack-problem/)
- [Bellman-Ford](/posts/algorithm-bellman-ford/)
- [Floyd-Warchall](/posts/algorithm-floyd-warchall/)

- [Memoization](/posts/algorithm-memoization/)

- 여행하는 외판원 문제
- Viterbi \| 비터비 알고리즘: 음성 인식, 합성에서 사용

## 💫 문제

---

DP 난이도 고점은 굉장히 높지만,  
코테 기준으로는 점화식 찾고, 초기값 설정하고, 반복문 돌면서 배열 채우면 끝이라 구현은 쉽다.  

다만,  
DP 많이 안풀어보면 문제에서 점화식을 찾아내는 과정이 어렵다.  
DP 많이 안풀어보면 DP로 푸는 문제인지 알아내는 것도 어렵다.  

= 많이 풀어볼 것.  

- [문제집](https://www.acmicpc.net/workbook/view/7319)
  - [1로 만들기](https://www.acmicpc.net/problem/1463)  

## 💫 비교 (부문제를 이용한 알고리듬)

---

### 🫧 vs DC

- 요약
  - 부문제 중복이 많으면, 미리 다 풀어두고 쓰는 DP
  - 부문제 중복이 적으면, 미리 풀어둔 부문제를 안써서 효율이 낮으니까 DC

- 공통점:
  - 순환적으로 정의된 문제로부터 출발

- Overlapping Subproblems \| 중첩된 부문제 특성 : 부문제들이 심하게 중복되는 문제

- DP
  - 부문제를 풀고 이를 이용하여 더 큰 문제를 해결하는 전략 -> 상향식
  - 똑같은 부문제는 딱 한 번만 풀어두면 되기 때문에, 똑같은 부문제가 많으면 많을수록 유리

- So, DP
  - 부문제 중복이 많을 때, 미리 다 풀어두고 다시 쓸 수 있으니까
  - i.e. 피보나치 수열 계산

- DC:
  - 큰 문제를 작은 문제로 쪼갠 후 부문제를 해결하려는 전략 -> 하향식
  - 귀납적 정의를 이용하여 부문제로 분할, 정복, 결합
  - 문제 자체를 나누고 푸는거라, 풀어둔 것들이 나중에 해답을 구할 때 다 쓰인다.
  - 같은 함수를 반복해서 순환 호출 (Like 재귀로 피보나치 구하기), 즉 부문제를 독립적으로 처리하기 때문에 똑같은 부문제도 매번 새로 풀어야 함

- So, DC
  - 부문제 중복이 적을 때, 미리 풀어둔 부문제를 안써서 효율이 낮으니까, 오히려 최종 해답에 쓰이지 않을 답을 미리 계산하느라 시간을 낭비하니까
  - i.e.: 합병 정렬, 퀵 정렬

### 🫧 vs Greedy

- 공통점:
  - 최적 부분 구조를 갖는 최적화 문제를 해결

- 최적 부분 구조: 문제의 최적해가 부문제의 최적해로부터 구성될 수 있는 성질
  - 쉽게 말해, 부문제의 최적해를 이용해서 전체 문제의 최적해를 구할 수 있는 성질

- Greedy
  - 최적해의 일부를 먼저 선택한 후 남은 부문제를 해결하려는 전략 -> 하향식
  - 각 단계에서 해답의 일부를 선택한 후 남은 부문제를 해결
  - 최적해를 보장한다는 증명만 되면 가장 효율적

- DP
  - 문제를 해결하기 위한 모든 대안들의 답을 구하고 그 가운데 최적의 해답을 찾음 -> 지능적인 무작위 기법, 상향식
  - 일반적인 문제 + 최적화 문제: 범용성

### 🫧 So

- 최적 부분구조를 갖는 최적화 문제를 해결하는데 사용
- 특히 부문제가 중첩되는 정도가 높을수록 유용
- 크기 별로 가능한 모든 문제를 미리 풀어놓고 재사용하기 때문에 지능화된 무작위 기법이라는 별칭
