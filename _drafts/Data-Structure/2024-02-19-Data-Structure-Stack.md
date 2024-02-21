---
title: "🌖 Stack"
date: 2024-02-19. 16:33
# last_modified_at: 2024-02-19. 17:59
last_modified_at: 2024-02-19. 20:03
categories: [⭐Computer, 🌖Computer-OS]
tags: [Data-Stucture, Stack]
---

## **💫 @TODO**

---

Stack 스택  
PUSH, POP  

한 쪽 끝에서만 원소를 넣어나 뺄 수 있는 자료구조  
Like 프링글스 통, 엘리베이터, 서류더미  

LIFO Last in First out  
(First in Last out)  

특정 위치에서만 원소를 넣거나 뺄 수 있는 제한된 자료구조  
스택 큐 덱  
Restricted Structure  

- 성질
  - 원소의 추가 O(1)
  - 원소 제거 O(1)
  - 제일 상단의 원소 확인이 O(1)
  - 제일 상단이 아닌 나머지 원소들의 확인/변경이 '원칙적으로' 불가능

배열 혹은 연결 리스트를 통해 구현할 수 있음  

배열을 이용한 구현 (연결리스트를 이용하는 것보다 더 쉬움)  

```cpp
const int MAX = 100005
int dat[MAX];
int pos = 0; // 다음 원소가 추가될 곳, 원소의 수

void push(int x)
{
	dat[pos++] = x;
}

void pop()
{
	// 굳이 dat[pos]를 변경할 필요가 없음
	// 어차피 다시 접근할 일도 없고, 나중에 들어올 때 새 값으로 덮어씌워 짐
	pos--;
}

int top()
{
	return dat[pos - 1];
}
```

```cpp
// STL stack

#include <bits/stdc++.h>
using namespace std;

int main(void)
{
	// push, pop, top, empty, size
	stack<int> S;
	S.push(10); // 10
	S.push(20); // 10 20
	S.push(30); // 10 20 30
	cout << S.size() << '\n'; // 3
	if(S.empty()) cout << "S is empty\n";
	else cout << "S is not empty\n"; // S is not empty
	S.pop(); // 10 20
	cout << S.top() << '\n'; // 20
	S.pop(); // 10
	cout << S.top() << '\n'; // 10
	S.pop(); // empty
	if(S.empty()) cout << "S is empty\n"; // S is empty
	cout << S.top() << '\n'; // runtime error 발생
}
```

수식의 괄호 쌍  
전위/중위/후위 표기법 (코테에서 나올 확률이 거의 0에 가깝다 (고 바킹독 센세가 판단))  
DFS  
Flood Fill  

호출스택 call stack  

스택 오버플로우  

<br>

<!-- ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ---- -->

### **🫧**

<br>

<!-- ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ---- -->
