---
title: "수식의 괄호 쌍"
# description: ""
categories: [💫Computer, 🌓PS-Algorithm]
tags: [Algorithm, Stack]
image: "/assets/img/background/kururu-lab.jpg"

date: 2024-02-22. 00:04
# last_modified_at: 2024-02-22. 22:41
last_modified_at: 2024-08-29. 21:37
---

{% include embed/youtube.html id='cdjjk-ryPKc' %}

## 💫 정의

---

`32 - {6 - (2 + 4) * 7}` -> `{()}` O  
`5 + {6 - (12 + 4} * 7)` -> `{(})` X  

주어진 괄호 문자열이 올바른지/균형잡혔는지 판단하는 문제.  

### 🫧 괄호가 한 종류일 때

- **안쪽부터 짝을 맞춰 지워나간다, 모두 지워진다면 올바른 문자열**
- 여는 괄호와 닫는 괄호 수를 비교한다, 수가 다르면 올바르지 않은 문자열
  - 수가 같다고 올바른 문자열인 것은 아님 (i.e. `))((`)

### 🫧 괄호가 여러 종류일 때

- **안쪽부터 짝을 맞춰 지워나간다, 모두 지워진다면 올바른 문자열**

### 🫧 관찰

문자열을 앞에서부터 읽어나갈 때,  
닫는 괄호는 남아있는 괄호 중에서 가장 최근에 들어온 여는 괄호와 짝을 지어 없애버리는 명령이라고 생각해도 된다.  

## 💫 Solve By [Stack](/posts/Data-Structure-Stack/)

---

### 🫧 왜 Why

**배열을 이용한 구현**  
최대 N번 중간 원소의 삭제가 발생 O(N<sup>2</sup>)  

**연결 리스트을 이용한 구현**  
O(N)  

### 🫧 구현

여는 괄호를 읽을 때 마다 저장하다가 닫는 괄호를 읽을 때 가장 최근에 들어온, 즉 가장 끝에 있는 여는 괄호의 짝을 이루게 해주고 pop를 하면 올바른 괄호 쌍인지 확인할 수 있다.  

1. 여는 괄호가 나오면 스택에 추가
2. 닫는 괄호가 나왔을 경우,
   1. 스택이 비어있으면 올바르지 않은 괄호 쌍
   2. 스택의 top이 짝이 맞지 않는 괄호일 경우 올바르지 않은 괄호 쌍
   3. 스택의 top이 짝이 맞는 괄호일 경우 pop
3. 모든 과정을 끝낸 후 스택에 괄호가 남아있으면 올바르지 않은 괄호 쌍, 남아있지 않으면 올바른 괄호 쌍

### 🫧 백준

- [Baekjoon-2504](/posts/Baekjoon-2504/)
- [Baekjoon-3986](/posts/Baekjoon-3986/)
- [Baekjoon-4949](/posts/Baekjoon-4949/)
- [Baekjoon-9012](/posts/Baekjoon-9012/)
- [Baekjoon-10799](/posts/Baekjoon-10799/)