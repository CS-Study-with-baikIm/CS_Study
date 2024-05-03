
## 이진트리의 개념
이진 트리란 자식을 **둘 이하** 가진 트리이다.

~~오늘 면접에서 코드를 만들 때 둘 이상으로 만들었다...~~

![](https://velog.velcdn.com/images/i-am-jiwon/post/a1db6c04-1f2b-469e-9de1-3ae411afc461/image.png)

위의 그림처럼
자식이 0, 1, 2까지는 모두 이진트리이고 자식이 3명이 되는 순간 이진트리가 아니다.

## 이진트리의 속성
- 이진트리에서 각 레벨에서 최대 노드의 수는 2^(레벨) 이다.
![](https://velog.velcdn.com/images/i-am-jiwon/post/fcb12789-6b7d-42a5-a0db-5b48c9a606ff/image.png)


- 특정 높이에서 가질 수 있는 최대 노드의 수는 레벨 0 일때를 제외하고 2^(높이) -1 이다. 레벨 0 은 1이다.
![](https://velog.velcdn.com/images/i-am-jiwon/post/6611068c-12d4-4935-8ce6-6d98a61f8e95/image.png)

## 이진트리 종류
- 전 이진트리 (Full Binary Tree or Strict Binary Tree)
모든 노드가 0 또는 2개의 자식 노드를 갖는 트리

- 완전 이진 트리 (Complete Binary Tree)
완전 이진 트리는 마지막 레벨을 제외하고 모든 레벨이 완전히 채워져 있는 트리
마지막 레벨은 꽉 차 있지 않아도 되지만 노드가 왼쪽에서 오른쪽으로 채워져야 한다.

- 포화 이진 트리 (Perfect Binary Tree)
포화 이진 트리는 모든 내부 노드가 두 개의 자식 노드를 가지며 모든 잎 노드가 동일한 깊이 또는 레벨을 갖는다

- 균형 이진 트리 (Balanced Binary Tree)
균형 이진 트리는 왼쪽과 오른쪽 트리의 높이 차이가 모두 1만큼 나는 트리

## Java에서 이진 트리 구현
#### 연결리스트
```java

public class Node {
    int value;
    Node left;
    Node right;

    public Node(int value) {
        this.value = value;
        left = null;
        right = null;
    }
}
```
위와 같이 노드를 데이터, 왼쪽 자식, 오른쪽 자식으로 구성할 수 있다.

