---
title: "인라이닝 Inlining, 인라인 함수 Inline Function"
# description: ""
categories: [💫Computer, 🌒Programming]
tags: [Computer, Programming, CPP, Inlining, Inline]
image: "/assets/img/background/kururu-lab.jpg"

date: 2022-10-01. 10:54
# last_modified_at: 2024-02-21. 18:30
# last_modified_at: 2024-02-23. 03:50
# last_modified_at: 2024-02-25. 04:13
last_modified_at: 2024-08-29. 21:33
---

## 💫 왜 Why

---

함수 호출 시에는 함수 호출 규약에 따라 약간의 [오버헤드](/posts/Overhead/)가 발생  

함수 호출 전 : 모든 레지스터 (CPU안의 저장 공간)가 저장되어야 하고 인수들을 복사해야 한다  
함수 호출 후 : 레지스터들이 다시 복구되어야 한다  

만약 아주 간단한 함수라면 함수 안의 문장을 실행하는 시간보다 함수 호출을 준비하는 시간이 더 걸릴 수 있다  

따라서 크기가 작은 함수의 경우에는 차라리 함수 호출을 하지 않고 코드를 복사하여서 넣어주는 편이 효율적일 수 있다  

## 💫 C++ inline

---

`inline` 키워드 (C++)  

함수 앞에 붙으면 컴파일러는 함수를 생성하지 않고 함수를 호출한 곳에 코드 넣어줌  
이를 인라인 함수 `Inline Function`  
함수를 인라인 함수로 만들면 함수 호출 오버헤드가 사라지므로 프로그램이 더 빠르게 실행될 수 있다.  

```cpp
inline void printHello()
{
	cout << "Hello";
}
```

멤버 함수를 클래스 내부에 정의하면 자동적으로 인라인 함수가 된다 (즉 호출이 멤버 함수 코드로 대치된다)  
멤버 함수를 클래스 외부에 정의하면 일반적인 함수와 동일하게 호출된다 (즉 스택에 인수들을 저장하고 복귀주소를 저장한 후에 멤버 함수로 제어가 이동한다)  

멤버 함수의 크기가 작은 경우, 클래스 내부에 정의하는 것이 좋다 (생성자, Getter, Setter 등)  
멤버 함수의 크기가 큰 경우, 코드 복사 시 실행파일의 크기가 커질 수 있으므로, 클래스 외부에 정의하는 것이 좋다  

## 💫 메모

---

최신 컴파일러는 알아서 가능한 영역까지 Inlining을 진행한다고 함

알아두면 좋지만 너무 신경쓰지는 말 것  
마이크로한 최적화는 장기적으로는 성능 향상에 큰 도움이 되지 않음 (좋은 코드에 신경써라)  
