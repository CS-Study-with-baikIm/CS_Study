## Stack(스택)
![](https://velog.velcdn.com/images/i-am-jiwon/post/a8c9803e-d9e9-46b3-a76e-6367d8d88288/image.png)

스택은 가장 마지막에 저장된 데이터가 가장 먼저 삭제되는 후입선출(LIFO, Last In FirstOut)의 구조이다.
스택은 한쪽 방향에서만 데이터의 삽입과 삭제가 가능하다.

스택 용어
- top(peek): 가장 최근에 저장된 데이터이자 먼저 삭제될 데이터이다.
- push: 데이터를 삽입하는 행동이다.
- pop: 데이터를 삭제하는 행동이며 가장 위에있는 데이터가 삭제된다.

예시
- 뒤로가기 및 실행 취소
- 재귀 함수

스택의 자료구조는 삽입과 삭제시 O(1), 탐색에는 O(n)의 시간복잡도를 가지게 된다.


## Queue(큐)
![](https://velog.velcdn.com/images/i-am-jiwon/post/90bbf929-f780-4ee4-9c36-9bbd82cf5b23/image.png)

한쪽에서 데이터 삽입, 반대쪽에서 데이터의 삭제가 가능한 선입선출(FIFO, First In First Out)의 구조이다.

큐 용어
- Enqueue: 데이터 삽입
- Dequeue: 데이터 삭제
- Front: Dequeu시 삭제되는 데이터(가장 앞에 있는 데이터)
- Rear: 추가될 새로운 요소의 위치

예시
- 줄서기, 재료의 재고관리(기한이 오래된 것 부터 사용)
- BFS
- 프린터의 대기열

큐의 자료구조는 삽입과 삭제시 O(1), 탐색에는 O(n)의 시간복잡도를 가지게 된다.

## Java
### Stack
```java
import java.util.Stack; //Stack 클래스 임포트 
```

```java
Stack<Number> stack = new Stack<>();	//Stack 생성
stack.push(1);							//1 넣기
stack.push(2);							//2 넣기
stack.push(3);							//3 넣기

stack.peek();							//최상단 요소인 3 가져오기, 제거 x

stack.pop();							//3 빼기
stack.pop();							//2 빼기
```
자바에서는 스택 자료 구조를 지양해야한다.
Vector 컬렉션을 상속받아 구현되었는데 이는 자바 1버전부터 있던 클래스로 취약점이 많기에 공식 문서에서도 Stack 클래스보다 Deque 클래스를 사용할 것을 권장한다.

Deque(덱)은 Stack과 Queue가 합쳐진 자료구조라고 볼 수 있다.
즉 양방향으로 삽입과 삭제가 가능하다.

#### Deque

```java
/* Deque를 Stack처럼 사용하기 */
Deque<String> stack = new ArrayDeque<>();

stack.push("1");	//1 넣기
stack.push("2");	//2 넣기
stack.push("3");	//3 넣기

stack.pop();		//3 빼기
stack.pop();		//2 빼기

```

### Queue
```java
import java.util.LinkedList;	//큐는 LinkedList를 활용
import java.util.Queue;
```

```java
Queue<Integer> queue = new LinkedList<>(); //Queue 생성, 큐는 링크드 리스트로 생성해야한다.

queue.offer(1);		//1 넣기
queue.offer(2);		//2 넣기
queue.offer(3);		//3 넣기

queue.peek();		//가장 앞 요소 1 가져오기, 제거 x

queue.poll();		//가장 앞 요소 1 반환, 제거 o
queue.poll();		//가장 앞 요소 2 반환, 제거 o

```
#### Deque
```java
/* Deque를 Queue처럼 사용하기 */
Deque<String> stack = new ArrayDeque<>();

stack.offer("1");	//1 넣기
stack.offer("2");	//2 넣기
stack.offer("3");	//3 넣기

stack.poll();		//1 빼기
stack.poll();		//2 빼기

```
