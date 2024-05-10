# Red-Black Tree란?
일종의 자기 균형 이진 탐색 트리(Self-Balancing BST)이다.
레드-블랙 트리는 이진 트리와 다르게 모든 노드들이 Red또는 Black이기 때문에 균형이 잡혀있고 최악의 경우에도 O(log n)이 보장된다.

![](https://velog.velcdn.com/images/i-am-jiwon/post/167a0214-6712-4f6d-a399-ca691a649bc2/image.png)


# 특징
1. 모든 노드가 빨간색 또는 검은색이다.
2. 루트 노드는 검은색이다.
3. 모든 리프노드(NIL)들은 검은색이다.
4. 빨간색 노드의 자식은 검은색이다.
5. 모든 리프 노드에서 Black Depth(리프에서 루트까지 가는 경로에서 만나는 검은색 노드의 개수)가 같다

# 데이터 삽입
1. 새로운 노드는 항상 빨간색이다.
![](https://velog.velcdn.com/images/i-am-jiwon/post/471559c1-7316-4f29-98f0-35fd014ac17e/image.png)

2. 빨간색이 연속으로 나타나는 Double Red를 해결하기 위한 2가지 방법

![](https://velog.velcdn.com/images/i-am-jiwon/post/05e1b089-fe27-46cf-b6cf-e6f625436951/image.png)


새로운 노드 N / 부모 노드 P / 조상 노드 G / 삼촌 노드 U일 때
삼촌 노드가 검은색일 경우 > Restructuring
삼촌 노드가 빨간색일 경우 > Recoloring

### - Restructuring
1. N, P, G를 오름차순으로 정렬
2. 셋 중  중간값을 부모로 만들고 나머지를 자식으로 만들기
3. 새로 부모가 된 노드를 검은색으로 만들고 나머지를 빨간색으로

![](https://velog.velcdn.com/images/i-am-jiwon/post/212434bb-cb75-4324-8674-8ff670097001/image.png)


### - Recoloring
1. N의 P, U를 검은색으로 바꾸고 G를 빨간색으로 변경
	1-1. G가 루트라면 검은색으로 변경
	1-2. Double Red가 발생하면 Restructuring, Recloloring진행 반복
    ![](https://velog.velcdn.com/images/i-am-jiwon/post/61eb003e-2501-4e62-92e2-7df67f7d8db1/image.png)
> **위처럼 검정색은 두번 나와도 가능하다. **

![](https://velog.velcdn.com/images/i-am-jiwon/post/8d203ff4-d26b-4651-9761-cb49aae2d599/image.png)

이런 경우에 Double Red를 해결해 줘야한다.

[RBT Java 참고 블로그](https://velog.io/@jakeseo_me/%EC%9D%B4%EA%B2%83%EC%9D%B4-%EC%9E%90%EB%B0%94%EB%8B%A4-%EC%B6%94%EA%B0%80-%EC%A0%95%EB%A6%AC-%EB%A0%88%EB%93%9C%EB%B8%94%EB%9E%99-%ED%8A%B8%EB%A6%AC-%EC%A0%95%EB%A6%AC)
