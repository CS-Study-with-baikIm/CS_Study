## Array(배열)
- 배열은 데이터들이 메모리에서 연속적으로 저장되어 있는 자료구조
- Index를 통해 접근이 용이하다.
- 크기는 처음 생성할 때 정하고 변경이 불가하다.

**시간 복잡도**
- 접근하고자 하는 인덱스를 알고 있을 때 / 배열의 끝에 삽입 및 삭제 : O(1)
- 순차적 탐색 / 끝을 제외한 배열의 삽입 및 삭제(삽입 후 데이터 이동) : O(n)



## Linked List(연결리스트)
- 여러개의 노드들이 순차적으로 연결된 형태를 갖는 자료구조
- 첫번째 노드(객체) head / 마지막 노드(객체) tail
- 각 노드(객체)는 데이터와 다음 노드(객체)의 주소로 구성되어있다.
- 연속적 메모리를 사용하지 않는다.
- 삽입과 삭제에 용이하다.
- Tree의 근간

**시간 복잡도**
- 탐색 : O(n)
- 삽입, 삭제 : O(1)
그러나 위치에 따라 탐색이 필요한 경우 : O(n)

![](https://velog.velcdn.com/images/i-am-jiwon/post/59364524-0c2d-425a-8c28-8b6b1ad208b7/image.png)

---
## Array vs Linked List
- Array은 연속된 메모리 / Linked List는 메모리상 떨어져있고 주소를 갖고있다.
- Array는 조회가 빠르다(O(1)) / Linked List는 느리다(O(n))
- Array는 추가 및 삭제 느리다(O(n)) / Linked List는 빠르다 (O(1))
- Array는 정적 메모리 할당 / Linked List는 동적 메모리 할당
- Array는 Stack에 메모리 할당 / Linked List는 Heap에 할당

---

## Java 에서 Array
**배열 선언**
```java
// 타입[] 변수;
int[] intArray;
String[] strArray;

// 타입 변수[];
int intArray[];
String strArray[];
```
**배열 생성**
```java
// 값 목록으로 생성
// 타입[] 변수 = {값1 ,값2, ...};
int[] intArray = {1, 2, 3};

// new 연산자로 배열 생성
// 타입[] 변수 = new 타입[길이];
int[] intArray = new int[]5;
```

**요소 얻기**
```java
int[] intArray = {1, 2, 3};

// 3번째 값 출력
System.out.println(intArray[2]);
```

---

## Java 에서 Linked List
**패키지 import**
```java
import java.util.LinkedList;
```
**LinkedList 객체 생성**
```java
// 타입설정 int 타입만 적재 가능
LinkedList<Integer> list = new LinkedList<>();

// 생성시 초기값 설정
LinkedList<Integer> list2 = new LinkedList<Integer>(Arrays.asList(1,2));
```
**LinkedList 요소 추가 / 삽입**
```java
LinkedList<String> list = new LinkedList<>(Arrays.asList("A", "B", "C")));

// 가장 앞에 데이터 추가
list.addFirst("new");

// index 1에 중간 위치에 데이터 10 추가
list.add(1, "new");

// 가장 뒤에 데이터 추가
list.addLast("new");
```
**LinkedList 요소 삭제**
```java
LinkedList<String> list = new LinkedList<>(Arrays.asList("A", "B", "C")));

// 첫 번째 값 제거
list.removeFirst();

// index 1 중간 위치 제거
list.remove(1);

// 마지막 데이터 제거
list.removeLast();

// 모든 값 제거
list.clear();
```
**LinkedList 요소 얻기**

```java
list.get(0); // 0번째 index 요소의 값 출력
```
