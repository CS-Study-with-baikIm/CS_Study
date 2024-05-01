# 배열 (Array)
배열은 입력된 데이터들이 메모리 공간에서 연속적으로 저장되어 있는 자료구조이다.

메모리 상에서 연속적으로 저장되어 있는 특징을 갖기 째문에, index를 통한 접근이 용이하다.

배열의 크기는 처음 생성할 때 정하며 이후에는 변경할 수 없다.


### 시간 복잡도
- 탐색 : O(1). 
   단, 접근하고자 하는 인덱스를 알고 있어야 한다. 

- 순차적으로 탐색시에는 O(n).

- 삽입 / 삭제 :
  - 배열의 처음 또는 중간에 삽입 및 삭제 : O(n)
(삽입 지점 이후의 데이터를 옮겨야 하기 때문.)
  - 배열의 끝에 삽입 및 삭제 : O(1)

# 연결 리스트 (Linked List)
연결 리스트는 여러 개의 노드들이 순차적으로 연결된 형태를 갖는 자료구조이며, 첫번째 노드를 head, 마지막 노드를 tail이라고 한다.

각 노드는 데이터와 다음 노드를 가리키는 포인터로 이루어져 있다.

배열과는 다르게 메모리를 연속적으로 사용하지 않는다.

배열과는 다르게 순차적으로 접근해야 하는 면에서 불리할 수도 있으나, 노드가 연결된 구조이기 때문에 삽입, 삭제에 용이하다.

Tree 구조의 근간이 되는 자료구조이며, Tree 에서 사용되었을 때 그 유용성이 드러난다.

### 시간 복잡도
#### 탐색 : O(n)

#### 삽입 / 삭제: 

- 삽입과 삭제 자체는 O(1)이다.

- 연결 리스트의 처음에 삽입/삭제 : O(1)

- 연결 리스트의 중간에 삽입/삭제 : O(n) (탐색시간 소요)

- 연결 리스트의 끝에 삽입/삭제 :
  - 끝을 가리키는 별도의 포인터를 갖는 경우 : O(1)
  - 끝을 가리키는 별도의 포인터를 갖지 않는 경우 : O(n) (탐색시간 소요)

## 배열과 연결 리스트 비교
### 장점
 - 배열 : 인덱스를 통한 빠른 접근 가능
 - 연결 리스트 : 삽입/삭제 용이
### 단점
- 배열 :
  - 삽입/삭제가 오래 걸림
  - 배열 중간에 있는 데이터가 삭제되면, 공간 낭비가 발생함
- 연결 리스트 : 
  - 임의 접근이 불가능하여, 처음부터 탐색을 진행해야 함

### 용도
  - 배열 : 빠른 접근이 요구되고, 데이터의 삽입과 삭제가 적을 때
  - 연결 리스트 : 삽입과 삭제 연산이 잦고, 검색 빈도가 적을 때

## Swift 단방향 연결 리스트 구현

### Node 구현

```swift

class Node<T> {
    var data: T?
    var next: Node?
    
    init(data: T?, next: Node? = nil) {
        self.data = data
        self.next = next
    }
}
```

### LinkedList 구현 및 CRUD 구현

```swift 
class LinkedList<T: Equatable> {
    private var head: Node<T>?

    // data append
    func append(data: T?) {
        
        //head가 없는 경우 Node를 생성 후 head로 지정해준다
        if head == nil {
            head = Node(data: data)
            return
        }
        
        var node = head
        while node?.next != nil {
            node = node?.next
        }
        node?.next = Node(data: data)
    }

    func insert(data: T?, at index: Int) {
        
        //head가 없는 경우 Node를 생성 후 head로 지정한다
        if head == nil {
            head = Node(data: data)
            return
        }
        
        var node = head
        for _ in 0..<(index - 1) {
            if node?.next == nil { break }
            node = node?.next
        }
        
        let nextNode = node?.next
        node?.next = Node(data: data)
        node?.next?.next = nextNode
        
    }
     

    func removeLast() {
        
        if head == nil { return }
        
     // head를 삭제하는 경우
        if head?.next == nil {
            head = nil
            return
        }
        
        var node = head
        while node?.next?.next != nil {
            node = node?.next
        }
        
        node?.next = node?.next?.next
        
    }

    func remove(at index: Int) {
        
        if head == nil { return }
        
        // head를 삭제하는 경우
        if index == 0 || head?.next == nil {
            head = head?.next
            return
        }
        
        var node = head
        for _ in 0..<(index - 1) {
            if node?.next?.next == nil { break }
            node = node?.next
        }
        
        node?.next = node?.next?.next
        
    }

    func searchNode(from data: T?) -> Node<T>? {
        
        if head == nil { return nil }
        
        var node = head
        while node?.next != nil {
            if node?.data == data { break; }
            node = node?.next
        }
        
        return node
    }
 

}
```

추가로 양방향 연결 리스트에 경우 각 노드에 tail을 추가해주고 양방향에서 각각 prev와 next를 이용하여 접근하면 된다
