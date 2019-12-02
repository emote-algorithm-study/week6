
# 그래프
 > 그래프는 유한하고, 하나 이상의 원소를 갖는 `Vertex 집합과` Vertex의 부분집합의 순서있는 쌍으로 이루어진 `Edge의 집합`으로 이루어진다.
 Edge는 Vertex의 쌍 (v1, v2)와 같이 나타내고, 방향그래프에서 순서는 유의미하다 
 
 
## 헷갈리는 그래프 관련 용어 정리
> `Adjacent` : 두 Vertex 간의 edge가 존재하는 것  
 `Reachable` : 두 Vertex 간의 path가 존재하는 것  
 
> `Connected` : Undirected Graph에서 임의의(모든) 두 node간 path가 존재하는 것  
  `Strongly Connected` : Digraph에서 임의의 두 node간 path가 존재하는 것
  
> `Symmetric Digraph` : 임의의 정점 Vi, Vj에 대해서 (Vi, Vj)가 존재할때 (Vj, Vi)도 존재하는 것  

> `Conneted Component` : 최대 연결 서브그래프 (Maximal connected subgraph)

</br>

# 그래프의 표현
  그래프를 컴퓨터에서 표현하는 방법은 두 가지가 있다.  
 첫번째는 `인접 행렬(Adjacency Matrix)`이고, 두번째는 `인접 리스트(Adjacency List)` 이다.

 ## 인접행렬의 구현
  인접행렬은 2차원 배열을 이용해 두 정점간 edge가 존재하는 경우 1, 존재하지 않는 경우 0으로 나타 내면된다.  
  ### 인접행렬의 장단점
  인접행렬은 두 정점이 인접한지 여부를  O(1)의 복잡도로 찾을 수 있으나,  
  연결되지 않은 edge가 많은 경우 공간 낭비가 많다.
  
 ## 인접리스트의 구현
  Vector의 배열을 이용해 구현한다.
``` C++
std::vector<int> adj_list[SIZE];  // 벡터의 배열
```
  위와 같이 벡터의 배열을 선언하고, 0번 정점에서 2번 정점으로 edge가 존재하는 경우
 ```C++ 
  adj_list[0].push_back(2)
 ```
  위와 같이 원소를 추가하면 된다.

  ### 인접리스트의 장단점
   인접리스트는 인접한 경우에만 원소를 가지기 때문에 필요한 공간만 차지한다는 장점이 있으나,  
   두 정점이 인접하는지 여부를 찾기위해 최악의 경우 O(V)의 시간 복잡도가 필요하다.
   
   
# DFS (Depth First Search)
 > 깊이 우선 탐색(DFS)는 시작 정점으로부터 거리가 먼 정점부터 방문하는 순회 방법이다.  
 
 ## DFS의 구현
  DFS는 `스택(Stack)`을 이용해 구현할 수 있다.  
  ```
  1. Stack이 빌때까지 아래 과정을 반복한다.
  2. (처음) 방문하는 노드를 스택에 넣는다.
  3. 방문한 노드에서 갈 수 있는 다른 노드가 있는 경우, 그 노드를 방문한다.  
  이때, 한번 방문한 노드는 표시해둔다.
  4. 방문한 노드에서 이미 모두 방문했거나, 더이상 갈 곳이 없는 경우, 스택에서 Pop한 후, Top인 노드로 Back tracking 한다. 
 ```
 

# BFS (Breath First Search)
 > 너비 우선 탐색(BFS)는 시작 정점으로부터 가까이에 있는 정점부터 방문하는 순회 방법이다.
 
  ## BFS의 구현
  BFS는 `큐(Queue)`를 이용해 구현할 수 있다.
  ```
  1. Queue 가 빌떄까지 아래 과정을 반복한다.
  2. 방문하는 노드에서 인접한 모든 정점을 큐에 넣는다.
  3. Queue의 front를 방문하고 Queue에서 삭제한다.  
```
  
