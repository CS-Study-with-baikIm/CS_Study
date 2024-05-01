# Stack

스택 자료구조는 차곡차곡 쌓아 올린 형태의 자료구조를 말하며, LIFO(Last in First Out) 방식의 자료구조이다.

### 스택의 특징

- 후입선출(LIFO, Last-In-First-Out)의 구조를 가진 자료구조
- 스택의 내부 동작 방식은 데이터의 삽입(push)과 제거(pop)가 동일한 쪽에서 이루어진다.
- 최상위 항목(top)에만 접근이 가능

### 스택 용어
- top(peek): 가장 최근에 저장된 데이터이자 먼저 삭제 될 데이터
- push: 데이터를 삽입하는 것
- pop: 데이터를 삭제할 때 사용

### 스택의 활용
- 웹 브라우저 방문기록 (뒤로가기)
- 실행 취소(undo)
- 역순 문자열 만들기
- 후위 표기법 계산
- 재귀 알고리즘
- 함수 호출

스택의 자료구조는 삽입과 삭제시에 O(1), 탐색에는 O(n)의 시간복잡도를 가진다.

## Swift에서 Stack 구현


```swift

struct Stack<T> {
    private var stack: [T] = []
    
    public var count: Int {
        return stack.count
    }
    
    public var isEmpty: Bool {
        return stack.isEmpty
    }
    
    public mutating func push(_ element: T) {
        stack.append(element)
    }
    
    public mutating func pop() -> T? {
        return isEmpty ? nil : stack.popLast()
    }
}
```
>사실 Swift에서 굳이 Stack을 만들어 사용하지 않아도, 배열 append, popLast 만으로도 충분히 배열을 Stack처럼 사용 가능하다

# Queue
가장 먼저 삽입된 데이터가 가장 먼저 삭제되는 자료 구조이다.
 FIFO(First In First Out) 방식의 자료구조 이다.

### 큐의 특징
- 선입선출(FIFO, Last-In-First-Out)의 구조를 가진 자료구조
- 큐의 내부 동작 방식은 데이터의 삽입은 최하위, 제거는 최상위 쪽에서 이루어진다.
- 최하위 항목(Front)에만 접근이 가능

### 큐 용어
- Enqueue: 데이터 삽입
- Dequeue (JS의 shift): 데이터 삭제
- Front: Dequeue시 삭제되는 데이터 (가장 먼저 저장된 데이터)를 가르킨다.
- Rear: 추가될 새로운 요소의 위치를 가르킵니다.

### 큐의 활용
- BFS 알고리즘
- 프로세스 관리 (JS의 콜백 큐)
- 프린터의 대기열

큐는 스택과 마찬가지로 삽입과 삭제에는 O(1), 탐색에는 O(n)의 시간복잡도를 가진다.

## Swift 에서 Queue 구현

```swift
struct Queue<T> {
    private var queue: [T] = []
    
    public var count: Int {
        return queue.count
    }
    
    public var isEmpty: Bool {
        return queue.isEmpty
    }
    
    public mutating func enqueue(_ element: T) {
        queue.append(element)
    }
    
    public mutating func dequeue() -> T? {
        return isEmpty ? nil : queue.removeFirst()
    }
}
 
```

>dequeue 작업에 경우 removeFirst() 함수가 array 의 첫 요소를 삭제 후 각 인덱스를 옮겨주는 작업이 포함되어 있으므로 Stack의 pop 에 비해 오랜 시간이 걸림

 #### 위 문제를 해결해주기 위해 구현된 Queue 도 존재함


```swift
struct Queue<T> {
    private var queue: [T?] = []
    private var head: Int = 0
    
    public var count: Int {
        return queue.count
    }
    
    public var isEmpty: Bool {
        return queue.isEmpty
    }
    
    public mutating func enqueue(_ element: T) {
        queue.append(element)
    }
    
    public mutating func dequeue() -> T? {
        guard head <= queue.count, let element = queue[head] else { return nil }
        queue[head] = nil
        head += 1
        
        // nil이 된 element를 삭제 시켜줌
        if head > 50 {
            queue.removeFirst(head)
            head = 0
        }
        return element
    }
}
 
```
head를 두고 queue의 element들을 Optional로 만들어 queue의 요소만 삭제시키고 그 공간은 유지시키고 head를 통해 요소에 접근하는 방식.

다만, 이 경우엔 빈공간이 생기므로 메모리 누수가 발생할 수 있어 빈 공간을 삭제 시키는 시간이 필요하고 그 과정으로 인해 Stack에 비해 시간이 발생할 수 밖에 없다.
