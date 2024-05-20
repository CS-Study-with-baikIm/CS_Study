# 그래프란
노드와 그 노드를 연결하는 간선을 하나로 모아 놓은 자료 구조

트리는 그래프의 일종이다. 하지만 그래프는 정점마다 간선이 존재하지 않을 수 있으며, 루트노트/자식노드와 같은 개념이 없다.
#### 그래프의 활용
실생활에서 지하철 노선도 최단경로, 도로 등에 사용되고 있다.

# 용어
- 정점(Vertex or Node) : 데이터를 저장하는 위치
- 간선(Edge) : 정점(노드)를 연결하는 선. 링크, 브랜치로도 불림
- 인접 정점(adjacent vertex) : 간선에 의해 직접 연결된 정점을 의미한다. 
- 단순 경로(simple path) : 경로 중에서 반복되는 정점이 없는 경우를 의미한다. 
- 차수(degree) : 무방향 그래프에서 하나의 정점에 인접한 정점의 수를 의미한다. 
- 진출 차수(in-degree) : 방향 그래프에서 외부로 향하는 간선의 수를 의미한다.
- 진입 자수(out-degree) : 방향 그래프에서 외부에서 들어오는 간선의 수를 의미한다.
- 경로 길이(path length) : 경로를 구성하는데 사용된 간선의 수를 의미한다. 
- 사이클(cycle) : 단순 경로의 시작 정점과 종료 정점이 동일한 경우를 의미한다.

# 종류
#### 무방향 그래프
![](https://velog.velcdn.com/images/i-am-jiwon/post/4b4de350-3f48-45ca-8c00-49a0d1610987/image.png)
>두 정점을 연결하는 간선에 방향이 없는 그래프

#### 방향 그래프
![](https://velog.velcdn.com/images/i-am-jiwon/post/80220768-18f8-4fa7-931a-e1f086d3eb0b/image.png)
>두 정점을 연결하는 간선에 방향이 존재하는 그래프
간선이 가리키는 방향으로만 이동 가능

#### 가중치 그래프
![](https://velog.velcdn.com/images/i-am-jiwon/post/af4292eb-257d-4dcf-8ab9-28fb1b4c6d78/image.png)
>두 정점을 이동할때 비용이 드는 그래프

#### 완전 그래프
![](https://velog.velcdn.com/images/i-am-jiwon/post/ff841ad4-e887-4806-a005-f7de60cae94e/image.png)
>모든 정점이 간선으로 연결된 그래프

#### 비연결 그래프
![](https://velog.velcdn.com/images/i-am-jiwon/post/1edcf4f3-7ea2-4aca-a9c0-658c113a4cd0/image.png)
>무방향 그래프에서, 연결 그래프가 아닌 그래프

# 장점
1. 복잡한 관계를 직관적으로 표현할 수 있다.
2. 네트워크 구조를 표현하는 문제를 다룰 수 있다.
3. 다양한 최적화 문제에 사용 가능하다.

# 단점
1. 규모가 커질수록 탐색 비용이 커진다.
2. 복잡하면 이해하기 어렵다.

# 그래프 구현 
## 1. 인접 행렬
인접 행렬이란 그래프의 정점을 2차원 배열로 만든 것이다.
직접 연결되어 있다면 1, 아니면 0을 저장
![](https://velog.velcdn.com/images/i-am-jiwon/post/42b1f23e-9582-441c-a4dd-c5dbd8042b29/image.png)

#### 장점
1. 2차원 배열에 모든 정점의 간선 정보가 있기에 조회에 O(1)의 시간복잡도
2. 구현이 쉽다.
#### 단점
1. 생성시에 O(n^2)의 시간복잡도가 소요된다.
2. 2차원 배열이므로 필요 이상의 공간 낭비가 있다.

## 2. 인접 리스트
인접 리스트는 그래프의 노드를 리스트로 표현한 것이다. 주로 정점의 리스트 배열을 만들어서 관계를 설정한다. 
![](https://velog.velcdn.com/images/i-am-jiwon/post/ed2fd42f-7f61-46b0-95d4-e41d6638b6d2/image.png)

#### 장점
1. 정점들의 연결 정보를 탐색할 때 O(n) 시간 복잡도가 소요된다. 
2. 공간 낭비가 적다.
#### 단점
1. 연결의 확인이 오래걸린다.
2. 구현이 어렵다.

## 선택 방법
- 인접 리스트
	- 그래프 내에 적은 숫자에 간선만 가지는 경우
    - 장점
    	1.어떤 노드에 인접한 노드를 쉽게 찾을 수 있다.
        2.그래프에 존재하는 모든 간선의 수는 O(N+E)안에 알 수 있다.
        
 - 인접 행렬
 	- 그래프에 간선이 많이 존재하는 경우
    - 장점
    	1.두 정점을 연결하는 간선의 존재여부를 바로 알 수 있다.
        2.정점의 차수는 O(N)안에 알 수 있다.
        
        
# 그래프의 탐색
## 깊이 우선 탐색(DFS, Depth-First Search)
DFS는 깊이 우선 탐색이라고 불리며 그 이유는 그래프의 시작점에서 다음 브랜치로 넘어가기 전에, 해당 브랜치를 모두 탐색하기 때문이다.

![](https://velog.velcdn.com/images/i-am-jiwon/post/96e14137-d6f7-48f3-ab08-f49980c2edc6/image.png)

**스택을 활용한 DFS의 동작 과정**
1. 시작점인 1번 노드를 스택에 넣고 방문처리를 한다.
2. 스택 최상단 노드(1번)와 미방문한 노드 중 가장 번호가 낮은 2번 넣고 방문처리
3. 스택 최상단 노드(2번)와 미방문한 노드(7번)를 스택에 넣고 방문처리
4. 스택 최상단 노드(7번)와 미방문한 노드 중 가장 번호가 낮은 6번 넣고 방문처리
5. 스택 최상단 노드(6번)와 미방문한 노드가 없을때는 추출(pop)
6. 스택 최상단 노드(7번)와 미방문한 노드(8번)를 스택에 넣고 방문처리
7. 이와같은 메커니즘으로 스택에 아무것도 없을때까지 반복

**구현**
```java
import java.util.Stack;

public class Main {
    static boolean[] vistied = new boolean[9];


    static int[][] graph = {{}, {2,3,8}, {1, 7}, {1, 4, 5}, {3, 5}, {3,4}, {7}, {2, 6, 8}, {1,7}};
    static Stack<Integer> stack = new Stack<>();

    public static void main(String[] args) {

        stack.push(1);
        vistied[1] = true;

        while(!stack.isEmpty()) {
            int nodeIndex = stack.pop();
            System.out.print(nodeIndex + " -> ");
            for (int LinkedNode : graph[nodeIndex]) {
                if(!vistied[LinkedNode]) {
                    stack.push(LinkedNode);
                    vistied[LinkedNode] = true;
                }
            }
        }
    }
}
```

**재귀함수를 활용**
재귀 함수란 자기 자신을 다시 호출하는 함수를 의미
만약 종료조건을 제대로 명시하지 않으면, 함수가 무한이 호출되기 때문에 종료조건이 있어야한다.
이러한 특성때문에 DFS를 구현하는데 재귀함수를 쓴다.
```java
public class Main {
    static boolean[] vistied = new boolean[9];


    static int[][] graph = {{}, {2,3,8}, {1, 7}, {1, 4, 5}, {3, 5}, {3,4}, {7}, {2, 6, 8}, {1,7}};
    public static void main(String[] args) {
        dfs(1);
    }

    static void dfs(int nodeIndex) {
        vistied[nodeIndex] = true;

        System.out.print(nodeIndex + " -> ");

        for (int node : graph[nodeIndex]) {
            // 인접한 노드가 방문한 적이 없다면 DFS 수행
            if(!vistied[node]) {
                dfs(node);
            }
        }
    }
}
```
## 너비 우선 탐색(BFS, Breadth-First Search)
루트 노드(혹은 임의의 다른 노드)에서부터 시작하여 인접한 노드를 먼저 탐색해 나가는 방법이다.
또한 BFS는 그래프에서 최단 경로를 찾는 정점 기반 알고리즘으로 유명하다.
BFS는 자료구조 큐(Queue)를 사용하여 구현 할 수 있다.

**특징**
- 직관적이지 않다.
- 재귀적 동작 x
- 방문여부를 반드시 검사

**큐를 이용하여 구현**
```java
import java.util.LinkedList;
import java.util.Queue;

public class Main {
    static boolean[] vistied = new boolean[9];

    static int[][] graph = {{}, {2,3,8}, {1, 7}, {1, 4, 5}, {3, 5}, {3,4}, {7}, {2, 6, 8}, {1,7}};


    public static void main(String[] args) {

        System.out.println(bfs(1, graph, vistied));
    }

    static String bfs(int start, int[][] graph, boolean[] visited) {
        StringBuilder sb = new StringBuilder();
        Queue<Integer> q = new LinkedList<>();

        q.offer(start);

        visited[start] = true;

        while(!q.isEmpty()) {
            int nodeIndex = q.poll();
            sb.append(nodeIndex + " -> ");
            for(int i=0; i<graph[nodeIndex].length; i++) {
                int temp = graph[nodeIndex][i];
                if(!visited[temp]) {
                    visited[temp] = true;
                    q.offer(temp);
                }
            }
        }
        return sb.toString() ;
    }
}
```
