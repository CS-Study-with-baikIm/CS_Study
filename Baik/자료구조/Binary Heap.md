# 힙(Heap)
힙(Heap)은 데이터에서 최대값과 최소값을 빠르게 찾기 위해 고안된 자료구조로, 완전 이진 트리(Complete binary tree)의 형태를 가진다.

이러한 힙은 힙 속성을 만족하는데, 힙 속성이란,

- 최대 힙 속성(max heap property) : 부모 노드의 키 값은 항상 자식 노드의 키 값보다 크거나 같다.
- 최소 힙 속성(min heap property) : 부모 노드의 키 값은 항상 자식 노드의 키 값보다 작거나 같다.
- 다음과 같으며, 어떤 힙 속성을 만족하는지에 따라 최대 힙(Max heap)과 최소 힙(Min heap)으로 나뉜다.

 

## 힙(Heap)의 특징

힙의 특징은 다음과 같다.

- 루트 노드(root node)는 항상 최댓값 또는 최솟값을 가진다 (만족하는 힙 속성에 따라)

- 부모-자식 사이의 크기 관계만 존재하며, 왼쪽 자식-오른쪽 자식 간의 크기 관계는 존재하지 않는다

- 완전 이진 트리이기 때문에 트리의 높이를 h라고 하면 h = |log2n| 이다.
이러한 힙은 힙 정렬, 우선순위 큐, 다익스트라 알고리즘 등에 응용된다.
 

## 힙(Heap)의 시간 복잡도
힙에서 최댓값(혹은 최솟값)을 참조함은 
O(1) 의 시간 복잡도를 가지며

원소를 삽입하거나 삭제 시 O(logN) 의 시간 복잡도를 가진다.

## 힙(Heap)과 이진 탐색 트리

힙과 이진 탐색 트리는 모두 이진 트리라는 공통점을 가지고 있기에, 겉으로 보기에는 별다른 차이점이 보이지 않는다.

그러나, 이 둘은 큰 차이점들을 가지고 있다. 차이점은 다음과 같다.



|  | 힙 | 이진 탐색 트리 |
| --- | --- | --- |
| 트리 형태 | 완전 이진 트리 | 이진 트리 |
| 원소의 중복 여부 | 중복 가능 | 중복 불가능 |
| 원소의 정렬 여부 | 정렬 X | 정렬 O |
| 원소 탐색 시간 복잡도 | O(n)(순차 탐색) | O(logN)(이진 탐색) |
| 원소의 삽입 및 삭제 시간 복잡도 | O(logN) | O(logN) / O(n) (skewed tree) |
| 최댓값/최솟값 참조 시간 복잡도 | O(1) | O(logN) / O(n) (skewed tree) |


## 힙(Heap)의 장점 및 단점
### 장점
1. 빠른 삽입 및 삭제 : Heap은 특정한 순서에 따라 정렬된 상태를 유지하므로 삽입과 삭제 연산이 상수 시간(O(log n))에 이루어진다. 이는 요소들의 우선순위에 따라 빠르게 작업을 처리할 수 있다는 것을 의미한다.

2. 우선순위 기반 작업 처리 : Heap은 우선순위 큐와 같은 다른 추상 자료형을 구현하는 데 사용된다. 최대 힙인 경우에는 가장 큰 우선순위를 가진 요소에 빠르게 접근할 수 있고, 최소 힙인 경우에는 가장 작은 우선순위를 가진 요소에 빠르게 접근할 수 있다. 이를 통해 우선순위에 따라 작업을 관리하고 처리할 수 있다.
 

### 단점
1. 임의 접근의 어려움 : Heap은 일반적으로 완전 이진 트리의 형태를 가지며, 배열 또는 연결 리스트를 사용하여 구현된다. 이러한 구조는 임의 접근을 지원하지 않고, 요소에 접근하기 위해 순차적인 탐색을 수행해야 한다. 따라서 특정한 요소를 찾는 데에는 O(n)의 시간이 걸린다.

2. 정렬 유지의 오버헤드 : Heap은 정렬된 상태를 유지하기 위해 삽입과 삭제 연산 시에 정렬을 조정해야 한다. 이는 일정한 오버헤드를 발생시킬 수 있다. 따라서 요소들의 정렬 상태가 항상 필요하지 않은 경우에는 다른 자료구조를 고려하는 것이 좋다.

3. 배열로 구현 시 추가적인 공간 요구 : Heap은 일반적으로 배열 또는 연결 리스트를 사용해 구현된다. 배열 기반의 Heap에서는 공간을 미리 할당해야 하므로 요소의 개수에 따라 적절한 크기를 선택해야 하며, 요소의 개수에 따라 추가적인 공간을 필요로 한다.

# 이진 힙(Binary Heap)
이진 힙은 힙 중에서 가장 널리 쓰이는 형태 중 하나로 이진 트리 형태인 힙이다. 이진 트리는 각 노드의 자식 노드가 반드시 2개 이하인 트리다. 이진 힙은 힙정렬 알고리즘을 위한 자료구조로서 1964년 J. W. J. 윌리엄이 발표하였다.

이진 힙은 완전 이진 트리라는 조건을 만족해야 한다. 완전 이진 트리는 모든 레벨의 노드가 채워져 있어야 하며, 마지막 레벨은 왼쪽부터 차 있어야 한다.

## 삽입(Insert)

힙에 원소를 추가하기 위해서 업힙이라는 작업을 수행해야 한다. 다음은 15를 최대 힙에 추가하는 과정이다.

1. 원소를 힙의 가장 마지막 노드에 추가.
![title](https://kayuse88.github.io/assets/img/posts/binary-heap/Heap_add_step1.svg)   


2. 추가한 원소를 부모와 비교. 순서가 힙 조건과 일치한다면 중지.
![title](https://kayuse88.github.io/assets/img/posts/binary-heap/Heap_add_step2.svg)  

3. 힙 조건과 순서가 맞지 않다면 부모와 위치를 교환. 힙 조건일 일치할 때까지 2~3번을 반복.
![title](https://kayuse88.github.io/assets/img/posts/binary-heap/Heap_add_step3.svg)  

## 삭제(Delete)
루트 노드는 힙의 종류에 따라 최대값 혹은 최소값을 가지게 됩니다. 따라서 최대값이나 최소값을 탐색할 때 걸리는 시간은 항상 O(1)이다. 값을 추출하고 다음 값을 루트로 만드는 작업을 다운힙이라 합니다. 다음은 최대 힙에서 삭제를 하는 과정이다.

1. 힙의 루트 노드를 삭제.
![title](https://kayuse88.github.io/assets/img/posts/binary-heap/Heap_delete_step1.svg)  

2. 마지막 노드를 루트로 이동. 루트를 자식 노드와 비교. 이 때, 두 자식 노드 중 최대 힙인 경우 더 큰 자식과 비교하며 최소 힙인 경우 더 작은 자식과 비교함. 순서가 힙 조건과 일치한다면 중지.
![title](https://kayuse88.github.io/assets/img/posts/binary-heap/Heap_delete_step2.svg)  

3. 만약 순서가 맞지 않는다면 위치를 교환. 힙 조건일 일치할 때까지 2~3번을 반복.
![title](https://kayuse88.github.io/assets/img/posts/binary-heap/Heap_delete_step3.svg)  


## Swift Heap


```swift
class BinaryHeap {
    
    var items = [Int]()
    
    init(_ val: Int) {
        items.append(val)
        items.append(val)
    }
    
// 삽입
    func percolate_up() {
        var i = items.count-1
        var parent = Int(i / 2)
        while parent > 0 {
            if items[i] < items[parent] {
                items.swapAt(i, parent)
            }
            i = parent
            parent = Int(i / 2)
        }
    }
    
    func insert(k: Int) {
        items.append(k)
        percolate_up()
    }
    
// 삭제
    func percolate_down(idx: Int) {
        let left = idx * 2
        let right = idx * 2 + 1
        var smallest = idx
        
        if left <= items.count-1 && items[left] < items[smallest] {
            smallest = left
        }
        
        if right <= items.count-1 && items[right] < items[smallest] {
            smallest = right
        }
        
        if smallest != idx {
            items.swapAt(idx, smallest)
            percolate_down(idx: smallest)
        }
    }
    
// 추출
    func extract() -> Int {
        let extracted = items[1]
        items[1] = items[items.count-1]
        items.popLast()
        percolate_down(idx: 1)
        return extracted
    }
}
```
