# 깊이 우선 탐색 알고리즘 (DFS Algorithm)
  
### **깊이 우선 탐색(DFS, Depth-First Search)**  
DFS는 깊이 우선 탐색이라고도 부르며 그래프에서 깊은 부분을 우선적으로 탐색 하는 알고리즘이다.  
DFS는 스택 자료구조 (혹은 재귀 함수)를 이용한다.  
루트 노드(혹은 다른 임의의 노드)에서 시작해서 다음 분기(branch)로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방법
미로를 탐색할 때 한 방향으로 갈 수 있을 때까지 계속 가다가 더 이상 갈 수 없게 되면 다시 가장 가까운 갈림길로 돌아와서 이곳으로부터 다른 방향으로 다시 탐색을 진행하는 방법과 유사하다.  
즉, 넓게(wide) 탐색하기 전에 깊게(deep) 탐색하는 것이다.  
사용하는 경우: 모든 노드를 방문 하고자 하는 경우에 이 방법을 선택한다.  
깊이 우선 탐색(DFS)이 너비 우선 탐색(BFS)보다 좀 더 간단하다.  
단순 검색 속도 자체는 너비 우선 탐색(BFS)에 비해서 느리다.  
  
**깊이 우선 탐색(DFS)의 특징**  
자기 자신을 호출하는 순환 알고리즘의 형태를 가지고 있다.  
전위 순회(Pre-Order Traversals)를 포함한 다른 형태의 트리 순회는 모두 DFS의 한 종류이다.  
이 알고리즘을 구현할 때 가장 큰 차이점은, 그래프 탐색의 경우 어떤 노드를 방문했었는지 여부를 반드시 검사 해야 한다는 것이다.  
이를 검사하지 않을 경우 무한루프에 빠질 위험이 있다.  
  
구체적인 동작 과정은 다음과 같다.  
1.탐색 시작 노드를 스택에 삽입하고 방문 처리를 한다.  
2.스택의 최상단 노드에 방문하지 않은 인접한 노드가 하나라도 있으면 그 노드를 스택에 넣고 방문 처리를 한다. 방문하지 않은 노드가 없으면 스택에서 최상단 노드를 꺼낸다.  
3.더 이상 2번의 과정을 수행할 수 없을 때까지 반복한다.  