# Red-Black Tree

레드-블랙 트리는 이진 탐색 트리의 일종으로, 자가 균형 이진 탐색 트리이다. 

이진 탐색 트리는 균형이 안맞을 경우, 최악 시간 복잡도는 O(N) 이다.

하지만, RB Tree는 삽입, 삭제 동안 트리의 모양이 균형 잡히도록 각 노드들은 Red 혹은 Black의 색상을 가지고 모든 경우에서 O(lonN)의 시간 복잡도를 보장받는다.

![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcitWfI%2FbtrptgRQlFi%2Fvd9FwY1WQKUpKDkjZWIGD1%2Fimg.png)   


## 레드-블랙 트리의 조건
1. 모든 노드는 빨간색 혹은 검은색이다.
2. 루트 노드는 검은색이다.
3. 모든 리프 노드(NIL)들은 검은색이다. (NIL : null leaf, 자료를 갖지 않고 트리의 끝을 나타내는 노드)
4. 빨간색 노드의 자식은 검은색이다.   == No Double Red(빨간색 노드가 연속으로 나올 수 없다)
5. 모든 리프 노드에서 Black Depth는 같다.   == 리프노드에서 루트 노드까지 가는 경로에서 만나는 검은색 노드의 개수가 같다.

## 레드-블랙 트리 삽입 과정

레드-블랙 트리를 쉽게 이해하려면, 예시를 들어 이해하는 게 가장 쉽다.
 
![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FblkAJy%2FbtrpiHjqbii%2Ftj9F3pQv8oZwVgD7ffX4w1%2Fimg.png)   


레드-블랙 트리에 새로운 노드를 삽입할 때 새로운 노드는 항상 빨간색으로 삽입한다. 

이렇게 되면 4번 조건이 위배되는 상황이 발생한다. 

즉, 빨간색 노드가 연속으로 2번 나타날 수 있다(Double Red)

레드 블랙 트리는 이러한 Double Red 문제를 해결하기 위해 2가지 전략을 사용한다.

![title](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbYG3yV%2FbtrpoxGRp6g%2FfBAd1VvrqdWy6QRRSKTX3k%2Fimg.png)   


앞으로 새로 삽입할 노드를 N(New), 부모 노드를 P(Parent), 조상 노드를 G(Grand Parent), 삼촌 노드를 U(Uncle)라고 하자. 즉, 삼촌 노드는 말 그대로 부모의 형제라고 생각하면 된다. 

Double Red가 발생했을 때 

- 삼촌 노드가 검은색이라면 -> Restructuring을 수행하면 된다.
- 삼촌 노드가 빨간색이라면 -> Recoloring을 수행하면 된다.

### Restructuring
Restructuring은 다음 과정을 거친다.
1. 새로운 노드(N), 부모 노드(P), 조상 노드(G)를 오름차순으로 정렬한다.
2. 셋 중 중간값을 부모로 만들고 나머지 둘을 자식으로 만든다.
3. 새로 부모가 된 노드를 검은색으로 만들고 나머지 자식들을 빨간색으로 만든다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FqszUV%2Fbtrpdq9Hhyf%2FHgbBFX55xi67E3JkjPpx7K%2Fimg.png)

위와 같은 상황을 가정하자. Double Red가 발생했는데 삼촌 노드가 검은색이다. 따라서 Restructuring을 수행한다.

먼저 새로운 노드 N과 부모 P, 조상 G를 오름차순으로 정렬한다. 그러면 3이 중간값이 된다.

![그림 5](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcAUx5F%2FbtrppAcjYXR%2FczbUJZ1GU22ufSGewtyYQ1%2Fimg.png)

따라서 중간값인 3을 부모 노드로 바꾸고 나머지 2와 5를 자식 노드로 바꾼다.

당연히 원래 5의 자식 노드였던 7은 딸려가게 된다.

 
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FMASjd%2Fbtrpq6WhqWJ%2F6Vg1qcMarQEqQDk1oKGi51%2Fimg.png)


마지막으로 새롭게 부모가 된 3을 검은색으로 바꿔주고 나머지 두 자식인 2, 5의 색을 빨간색으로 바꿔주면 Double Red 문제가 해결된다!

여기서 완성된 트리가 규칙 3(모든 리프 노드는 검은색)을 만족하지 않는 것처럼 보일 수 있다. 값이 2인 노드는 자식 노드 NIL 2개를 가지고 있고 그 NIL들이 검은색이라고 생각하면 된다.

### Recoloring
Recoloring은 다음과 같은 과정을 거친다.

1. 새로운 노드(N)의 부모(P)와 삼촌(U)을 검은색으로 바꾸고 조상(G)을 빨간색으로 바꾼다.   
  
    1-1. 조상(G)이 루트 노드라면 검은색으로 바꾼다.   

    1-2. 조상(G)을 빨간색으로 바꿨을 때 또다시 Double Red가 발생한다면 또다시 Restructuring 혹은 Recoloring을 진행해서 Double Red 문제가 발생하지 않을 때까지 반복한다.



![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdWUP6r%2Fbtrpjv39bFN%2FH0wFIBAK3bV3cDrG5PwH4K%2Fimg.png)


위와 같은 상황을 가정하자. Double Red가 발생했는데 삼촌 노드가 빨간색이다. 따라서 Recoloring을 수행한다.

먼저 부모(P)와 삼촌(U)을 검은색으로 바꾸고, 조상(G)을 빨간색으로 바꾼다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fnkkuw%2Fbtrpjvpzukc%2FZprBjMgiPVQzBJxPgaZiU1%2Fimg.png)


하지만 루트 노드는 검은색이라는 조건을 지켜야 하므로, 루트 노드를 검은색으로 바꾼다.

이렇게 하면 모든 조건이 지켜지면서 Double Red 문제가 해결된다.

검은색 노드는 2번 나와도 되냐고 묻는다면 Yes이다. 빨간색 노드가 2번 나오면 안 되는 것이다. 
 
Recoloring은 간단해 보이지만 문제는 조상 노드(G)가 루트 노드가 아니면서, 조상 노드(G)가 또다시 Double Red 문제가 발생하는 경우이다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FvBBus%2FbtrpjwouNiw%2FcBnlbiBxKyKUb8XRBvf4D1%2Fimg.png)


위와 같은 상황을 가정하자. 왼쪽 트리에서 Recoloring을 진행하면 오른쪽 트리가 된다.

이때 조상 노드(G)가 또다시 Double Red가 발생하게 된다.
 
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbawsxN%2FbtrpoyMAmYw%2F3KxRGRUuFwJU5KTsmkwNJ0%2Fimg.png)


Double Red 문제가 발생한 "값이 5인 노드"를 기준으로 다시 한번 살펴보자.

해당 노드의 삼촌(U)이 빨간색이므로 다시 Recoloring을 진행해주면 Double Red 문제를 해결할 수 있다!

만약 해당 노드의 삼촌(U)가 검은색이었다면 Restructuring을 진행해주면 된다.
