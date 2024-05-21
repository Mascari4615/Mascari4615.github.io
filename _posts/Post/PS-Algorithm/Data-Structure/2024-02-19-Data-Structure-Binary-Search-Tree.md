---
title: "🌓 Binary-Search-Tree"
date: 2024-02-19. 20:52
# last_modified_at: 2024-02-19. 20:52
categories: [⭐Computer, 🌓PS-Algorithm]
tags: [Data-Stucture, Heap]
---

## **💫 @TODO**

---

Binary-Search-Tree  
이진 탐색 트리  

이진 탐색 개념을 그래프의 트리 구조 사용하여 표현  
마찬가지로 각 노드는 최대 두 개의 자식 노드를 가짐  

- 성질
  - 모든 노드는 왼쪽 가지에 포함되는 어떤 숫자보다 큰 숫자
  - 모든 노드는 오른쪽 가지에 포함되는 어떤 숫자보다 작은 숫자
  - -> 따라서 최상단 노드로부터 왼쪽 가지만 쭉 따라가면 최소노드 (최솟값)이 나옴
  - -> 따라서 최상단 노드로부터 오른쪽 가지만 쭉 따라가면 최대노드 (최댓값)이 나옴

추가  

1. 최상단 노드부터
2. 추가하려는 노드가 현재 노드 값과 비교해서 작으면 왼쪽, 크면 오른쪽으로 진행
3. 더 이상 비교할 수 없으면 정착 (비어있는 곳에 새로 추가해야 하는 상황)

삭제  

1. 자식 노드가 없으면 대상 노드만 삭제하면 끝
2. 자식 노드가 하나면 자식 노드를 기존 노드 위치로 이동
3. 자식 노드가 두 개 이상이면, 삭제한 노드의 왼쪽 가지에서 최대 노드를 찾아 (혹은 오른쪽 가지에서 최소 노드를 찾아) 기존 노드 위치로 이동
   - 이동한 자식 노드가 자식 노드를 가지고 있으면, 해당 노드에 대해 3번 재귀적 반복

탐색  

1. 최상단 노드부터
2. 찾으려는 숫자가 현재 노드와 비교해서 작으면 왼쪽으로, 크면 오른쪽으로 진행

탐색, 추가할 때의 최적의 위치는 찾는 과정,  
트리의 높이 (깊이 또는 단계) 만큼만 비교하면 되므로 노드가 n개 있고 트리가 균형잡힌 경우라면 최대 Log<sub>2</sub>N회의 비교로 이동할 수 있습니다.  

단, 트리가 치우쳐서 직선에 가까운 모양인 경우에는 트리가 높아져서 O(N)이 될 수도 있음  

- 확장
  - 자가 균형 이진 탐색 트리 Self-Balancing Binary Search Tree
    - 항상 균형을 유지하는, 탐색 효율을 유지할 수 잇음
  - B 트리
    - 자식 수를 m개로 확장해서 자식 수에 제한을 두지 않고 트리의 균형을 도모한 B트리

<br>

<!-- ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ---- -->

### **🫧**

<br>

<!-- ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ----  ---- ---- ---- ---- -->