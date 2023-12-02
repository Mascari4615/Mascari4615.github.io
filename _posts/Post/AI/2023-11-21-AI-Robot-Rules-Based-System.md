---
title: "🌗 전문가 시스템 - Rules-Based System"
date: 2023-11-21 10:43
last_modified_at: 2023-11-22 15:57
categories: ⭐Computer 🌗AI
tags: AI Rules-Based-System
---

@ GPT의 문제점 : 기업 정보가 OPEN AI로 유출된다, 그래서 못쓰게 한다, 근데 쓰고는 싶어서 직접 만들어 쓴다  

## 💫 전문가 시스템 - Rules-Based System

---

기호주의, 기호, Symbol을 처리한다 논리 p → s  
단순한 기호, 논리 가지고는 표현이 안되겠다  

지식을 가지고 표현을 해야겠다 !  

지식 기간 시스템 여러 가지 시도  
i.e. 프레임  
각자 자기가 알고 있는 Some에 대한 사실들과 연산들이 묶여서 표현되어야 한다 = 개체지향  

근데 인간이 가지고 있는 지식이 너무 많아, 컴퓨터에 다 못 들어가, 병목현상이 있다  
특히 당시만 하더라도 용량이 굉장히 작아  

다 잘하는 인공지능을 만들지 말고 특정한 일을 잘하는 AI를 만들자 → 전문가 시스템  
최초로 상업적으로 성공한 AI SYSYEAM이 된다 → AI BOOM  

Like 알파고 시리즈  

알파고 (탐색 시스템이면서 전문가 시스템, + 딥러닝, 강화학습 = 하이브리드), 알파제로.. 범용적으로  
알파제로, 알파게임, 혹은 코딩 잘하는.. 다시 세분화  
Chat GPT.. 다시 범용적으로 ← 전문가시스템 한계 극복

---

기호주의로 부터 시작된 지식기반 시스템  

딥러닝을 이용한 패턴 인식 시스템이나, GPT같은 거대한 지식  
이를 인코딩하는 방법, 지식이 저장되어 있는 방식 -> 신경망의 가중치  

## 💫 구조, 처리 단계

---

작업 메모리 Working Memory (Facts 사실, Data)  
→ 처음엔 비어있다가, 사실들을 저장  

지식 베이스 Rule Memory (Rules 규칙/지식, Program)  
→ 이미 가지고 시작하는  

추론 엔진 (Executive)  
→ 추론 : inferance, chaning, 연쇄  

### 🫧 Match

Fact, i.e. 아픈 사람이 왔다  

추론엔진의 Match  

지식 베이스에서 if (아픈사람이 왔다), 다시말해 내가 아는 지식에 아픈사람에 대한 대처가 있다 한다면 처리  
Facts 사실과 그 사실을 처리할 수 있는 Rules를 찾는 일  

Facts와 매칭되는 Rules가 여러 개라면, Conflict Set이 발생할 수 있다.  

### 🫧 Conflict Resolution (Restrove) - 충돌 해소

일반적으로 처음 만나는 Rule을  

### 🫧 Single Rule Trigger (Fire) - 규칙 적용/점화

그렇게 처리 Fire를 하면, 더 이상 아픈사람이 왔다 라는 건 사실이 아님, 대신 새로운 사실 -> 더 이제 안 아픈 사람이 있다 라는 사실  

반복한다.  

### 🫧 알파고의 동작?

수를 두는 것이 Fact가 되고, 이 Fact에 맞는 추론을 딥러닝과 강화학습 등과 같은 추가적인 기술을 붙여 진행한다.  

## 💫 추론

---

### 🫧 전방향추론 - Forward Chaining

지식, 규칙의 형태, p -> s, s -> r 같은.. (지식 베이스)
사실 (워킹 메모리)  

(빨간줄, 잘 기억해야 됩니다)
알려진 사실로부터 `새로운 사실 생성`  

사실이 많이 만들어지면, 쓸데없는 것들도 많겠죠  

### 🫧 후방향추론 - Backward Chaining

근데 우리가 추론할때는  
증상을 물어보고 추론을 하겠지만, 많은 경우에는 사실 가정을 한다 (감으로)

내가 돈을 받아야 하나? → 대처를 했는지 확인
대처를 했나? → 아픈 사람이 있는지 확인

알고 싶은 걸 정해두고, 그거에 되기 위한 규칙을 알아내는 것  
p → q 에서 q를 정해두고, p를 찾는것
`가설 증명`  

### 🫧 양방향추론 - Bidirectional Chaining

현실세계에서의 추론  

## 💫 결함 포용(/수용/허용) - Fault Tolerance

---

Tolerance, 견딜 수 있는 한계  
결함/오류가 있어도 감당하겠다. (시스템이 다운되지 않는다.)  

i.e. 백업, 백섭, 분산 저장소  