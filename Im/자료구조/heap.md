
# Heap(힙)

#### 트리 기반 자료구조이며 두 가지 종류가 있다.

1. 최대 힙 (부모가 자식보다 큰 값을 갖는다)
- 루트노드가 항상 제일 큰 값이다.
- 부모 자식간의 크기만 비교한다. (형제 노드 대소비교 x)

![](https://velog.velcdn.com/images/i-am-jiwon/post/c06b5532-8b9b-44db-add7-71aeb0dba9d4/image.png)

2. 최소 힙 (부모가 자식보다 작은 값을 갖는다)
- 루트노드가 항상 제일 작은 값이다.
- 부모 자식간의 크기만 비교한다. (형제 노드 대소비교 x)
![](https://velog.velcdn.com/images/i-am-jiwon/post/88e2f65f-18fe-492c-81ed-85d4e403b01a/image.png)

이러한 특성으로 최댓값, 최솟값을 빠르게 찾아낼 수 있어 우선순위 큐를 구현하는데 적합한 자료구조이다.



# Binary Heap(이진 힙)
### 개요
- 가장 널리 쓰이는 힙의 형태
- 이진 트리의 형태
- 이진 힙은 완전 이진트리의 조건 만족(모든 레벨의 노드가 채워져있어야 하며 마지막 레벨은 왼쪽부터)

### 장단점
장점
- 빠른 삽입/삭제 연산
- 우선순위 큐와 힙 정렬에 유용

단점
- 자식 노드의 값 배열이 무작위이며 중복이 가능하기 때문에 이진 탐색을 지원하지 않음
- 메모리 사용량이 많을 가능성 있음

### 시간복잡도
삽입 : O(log n)
삭제 : O(log n)
> 이동을 하기 때문에 힙의 높이만큼 삽입과 삭제 연산이 일어나기 때문

최대/최소값 검색 : O(1)
> 루트노드이다.

### 삽입
1. 힙의 끝에 최솟값 삽입(힙이 완전 이진트리이기 때문)
2. 힙의 조건에 맞을 때 까지 위치 바꾸기(최소- 부모가 작아야함 / 최대- 부모가 커야함)
![](https://velog.velcdn.com/images/i-am-jiwon/post/d42bb4bd-90be-4ddb-bbd9-d63548fc04cb/image.png)


### 삭제
1. 삭제하려는 값을 최대로 만들어 루트에 위치
2. 루트노드 삭제
3. 마지막 노드 루트로 이동
4. 힙의 조건에 맞을 때 까지 위치 바꾸기(최소- 부모가 작아야함 / 최대- 부모가 커야함)
![](https://velog.velcdn.com/images/i-am-jiwon/post/f2ef2e2b-10d2-47af-ae6a-94c3d5d14a77/image.png)

### Java

자바에서는 priority queue를 이용해 쉽게 힙을 구현할 수 있다.
```java

PriorityQueue<Integer> minHeap = new PriorityQueue<>();

PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());


```
