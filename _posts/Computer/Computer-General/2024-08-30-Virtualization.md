---
title: "Virtualization"
# description: ""
categories: [💫Computer, 🌚Computer-General]
tags: [Computer, Virtualization]
image: "/assets/img/background/kururu-lab.jpg"

date: 2024-08-30. 00:22
last_modified_at: 2024-08-30. 00:22
---

## 💫 Virtualization 가상화

---

물리적인 리소스를 추상화하여 논리적인 리소스로 변환하는 기술  

보통 물리적인 리소스 하나를 여러 개의 논리적인 리소스로 분할  
물리적인 하드웨어의 효율적으로 극대화할 수 있게  

### 🫧 이점

- 자원 효율성 : 물리적 하드웨어의 사용률을 극대화하여 자원을 효율적으로 사용
  - 비용 절감 : 하드웨어 자원의 효율적인 사용으로 인해 비용 절감
- 유연성 : 필요에 따라 가상 리소스를 쉽게 생성, 삭제, 이동할 수 있어 유연한 자원 관리가 가능
- 격리성 : 각 가상 리소스가 독립적으로 운영되므로, 하나의 리소스에서 발생한 문제가 다른 리소스에 영향을 미치지 않음
  - 하나의 스레드가 무한 루프에 걸려도, 다른 스레드에 영향을 주지 않음.

### 🫧 사용

- 서버 가상화 : 하나의 물리적 서버를 여러 개의 가상 서버로 분할하여 각각 독립적으로 운영
- 가상 메모리 (메모리 가상화) : 메모리가 없는데 있는척 하는것, 메모리가 적은데 디스크를 써서 많은척 하는 것
- CPU 가상화 : CPU가 없는데 있는척 하는것

### 🫧 예시 : 서버 가상화

서버 -> 가상 머신  
물리적 서버 1대 -> 가상 머신 3대 (각각 독립적인 운영 체제와 애플리케이션 실행)  

각 가상 머신은 독립적인 운영 체제와 애플리케이션을 실행할 수 있으며,  
물리적 서버의 CPU, 메모리, 디스크 등의 자원을 공유 (공유자원).

## 💫 참고

---

[참고 : 'IBM - 가상화란?'](https://www.ibm.com/kr-ko/topics/virtualization)  