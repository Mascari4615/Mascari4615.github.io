---
title: "🌓 BFS"
date: 2024-02-23. 03:30
# last_modified_at: 2024-02-23. 17:29
last_modified_at: 2024-03-22. 01:03
categories: [⭐Computer, 🌓PS-Algorithm]
tag: [Algorithm, Search, BFS, Breadth-First-Search]
---

{% include embed/youtube.html id='ftOmGdm95XI' %}

## **💫 정의**

---

BFS Breadth First Search  
다차원 배열에서 각 칸을 방문할 때 너비를 우선으로 방문하는 알고리듬  

너비를 우선으로 방문?  
설명할 방법이 없다  

원래 BFS는 그래프라는 자료구조에서 모든 노드를 방문하기 위한 알고리듬  
그래프 : 정점과 간선으로 이루어진 자료구조  
<br>

## **💫 구현**

---

다차원 배열에서의 BFS  

BFS에는 자료를 담을 큐가 필요하다  
알고리듬이 시작되면 우선 (0, 0)에 방문했다는 표시를 남기고 해당 칸을 큐에 넣어요  
이 초기 세팅이 끝난 후에는 큐가 빌 때까지 계숙 큐의 front를 빼고 해당 좌표의 상하좌우를 살펴보면서 방문하지 않는 칸을 큐에 넣어주는 작업을 반복  
큐가 빈 순간 과정은 종료  

1. 시작하는 칸을 `큐`에 넣고 방문했다는 표시를 남김
2. `큐`에서 원소를 꺼내어 그 칸에 상하좌우로 인접한 칸에 대해 3번을 진행
3. 해당 칸을 이전에 방문했다면 아무 것도 하지 않고, 처음으로 방문했다면 방문했다는 표시를 남기고 해당 칸을 `큐`에 삽입
4. `큐`가 빌 때까지 2번을 반목
방문 표시를 남기기 때문에 모든 칸이 `큐`에 1번씩 들어가므로 시간복잡도는 칸이 N개일 때 O(N).  
행이 R개이고 열이 C개이면 O(RC)  

어느정도 정석적인 구현  

```cpp
#include <bits/stdc++.h>

using namespace std;

#define X first
#define Y second // pair에서 first, second를 줄여서 쓰기 위해서 사용

int board[502][502] = {
	{ 1, 1, 1, 0, 1, 0, 0, 0, 0, 0} ,
	{ 1, 0, 0, 0, 1, 0, 0, 0, 0, 0} ,
	{ 1, 1, 1, 0, 1, 0, 0, 0, 0, 0} ,
	{ 1, 1, 0, 0, 1, 0, 0, 0, 0, 0} ,
	{ 0, 1, 0, 0, 0, 0, 0, 0, 0, 0} ,
	{ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0} ,
	{ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0} }; // 1이 파란 칸, 0이 빨간 칸에 대응
bool vis[502][502]; // visit 해당 칸을 방문했는지 여부를 저장
int n = 7, m = 10; // n = 행의 수, m = 열의 수

int dx[4] = { 1, 0, -1, 0 };
int dy[4] = { 0, 1, 0, -1 }; // 상하좌우 네 방향을 의미

int main(void)
{
	ios::sync_with_stdio(0);
	cin.tie(0);

	queue<pair<int,int>> Q;

	vis[0][0] = 1; // @ (0, 0)을 방문했다고 명시
	Q.push({ 0, 0 }); // 큐에 시작점인 (0, 0)을 삽입.
	
	while(!Q.empty())
	{
		pair<int,int> cur = Q.front();
		Q.pop();
		
		cout << '(' << cur.X << ", " << cur.Y << ") -> ";
		
		// 상하좌우 칸을 살펴볼 것이다.
		for (int dir = 0; dir < 4; dir++)
		{ 
			// nx, ny에 dir에서 정한 방향의 인접한 칸의 좌표가 들어감
			int nx = cur.X + dx[dir];
			int ny = cur.Y + dy[dir];

			// @ 아랫조건보다 먼저, 범위 밖일 경우 넘어감
			if (nx < 0 || nx >= n || ny < 0 || ny >= m)
				continue; 
			// 이미 방문한 칸이거나 파란 칸이 아닐 경우
			if (vis[nx][ny] || board[nx][ny] != 1)
				continue;

			// (nx, ny)를 방문했다고 명시
			// @ 넣을때 표시하지 않고, 뺄 때 표시한다면 중복된 요소가 큐에 들어갈 수 있어서 메모리 초과, 시간 초과가 날 수 있다
			vis[nx][ny] = 1; 
			Q.push({ nx, ny });
		}
	}
}
```

<br>

## **💫 메모**

---

- 그림판에서 페인트(통) 기능
- 외부 윤곽석을 따라 구분되는 영역의 색을 한 번에 바꾸는 기능

- Flood Fill
- 거리측정 (최단거리)
  - 방문 표시 대신 시작점과의 거리
  - -1로 초기화하면 방문 표시 여부도 알 수 있다
- 시작점이 여러 개
  - 여러 시작점을 큐에 다 넣으면 됨
  - BFS 성질 -> 큐에는 요소가 거리(시간) 순서대로 들어감 (큐에 요소가 쌓이는 순서는 거리 순)
- 시작점이 두 종류
  - 모두 BFS를 돌림
  - 하나를 먼저 BFS. 순서를 다르게 할 수 있다면 (전파가 서로 영향을 주지 않으면, 한쪽만 영향을 준다면)
  - 전파가 서로 영향을 준다면 -> 백 트래킹
- 1차원에서의 BFS
  - 단순히 전파가 좌우로만 이루어지는

<br>
