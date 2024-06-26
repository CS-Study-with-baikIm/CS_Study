# 프로세스(Process)
> **실행중인 프로그램을 의미하며, 운영체제에 의해 관리되고 독립적으로 실행되어 자원을 할당 받을 수 있는 단위**

### 구조
![](https://velog.velcdn.com/images/i-am-jiwon/post/dc313c69-1873-44e5-8ffa-6ea5ee2cd446/image.png)
프로세스는 각각의 독립된 메모리(Code, Data, Stack, Heap)영역을 할당 받는다.

1. code
- 작성한 코드가 저장되는 공간, 코드는 0과 1로 변환된 기계어가 저장됨

2. data
- 코드에서 선언된 전역변수, static변수, 상수 등이 저장됨
- 초기화된 변수와 아닌 변수가 나누어 저장됨
- 프로그램 시작 시 초기화, 프로세스 끝날 때까지 유지

3. stack
- 지역변수, 매개변수, return 주소들을 저장
- 함수가 호출되면 stack공간이 생기고, 함수가 종료되면 제거

4. heap
- 동적으로 생성되는 데이터 구조, 객체들 저장
- 프로세스의 주소 공간의 나머지 영역에 위치하며, 크기는 동적으로 확장 가능

### 프로세스의 상태
![](https://velog.velcdn.com/images/i-am-jiwon/post/d6805889-9dc3-48bc-bd2f-85cb121f1cef/image.png)

1. 프로세스 생성(new) : 생성되었지만 자원을 할당 받지 못한 상태
2. 실행 가능(Ready) : 자원을 모두 할당받았지만 CPU를 할당받지 못한 상태, Queue에서 대기
3. 실행 상태(Running) : 프로세서를 차지하여 명령들이 실행중
4. 대기(Blocked) : 이벤트가 발생하여 잠시 멈춘 상태, CPU를 사용하지 않는다.
5. 종료(Terminated, exit) : 메모리 공간은 운영체제에 반환

# 쓰레드(Thread)
> **프로세스의 실행 단위로 실제 작업을 수행하는 주체, CPU에 작엽 요청하는 실행 단위**

![](https://velog.velcdn.com/images/i-am-jiwon/post/867fdc4f-e358-4419-9704-6d26ea23047f/image.png)

### 특징
1. stack만 할당받고 나머지 영역은 공유한다.
2. 프로세스 내의 주소 공간이나 자원들을 같은 프로세스 내 쓰레드끼리 공유하며 실행
3. 쓰레드가 프로세스 자원을 변경하면 다른 쓰레드도 그 결과를 즉시 볼 수 있다.

### 장점
1. 응답성 향상 : 병렬처리로 인해 사용자가 응용 프로그램을 사용할 때 빠른 응답성을 제공
2. 자원 공유 효율성 향상 : 프로세스 내부 자원을 공유하기에 별도 메모리 공간 할당이 필요 없다.
3. 동시성 : 어러 쓰레드를 동시에 실행 할 수 있다.
4. 간결성 : 작업을 분리할 수 있어 코드가 간결함

### 단점
1. 스레드 간의 간섭 : 서로에게 영향을 미치기에 예상하지 못한 이슈 발생 가능
2. 성능 저하 : 쓰레드를 많이 생성하면 컨텍스트 스위칭이 빈번하게 발생하여 성능 저하가 일어날 수 있다.
3. 동기화 이슈 : 동시에 접근할 대 동기화 문제가 발생할 수 있다.
4. 자원 소비 : 개별적 흐름을 갖기에 쓰레드 마다 stack자원을 소비한다.

# 프로세스 vs 쓰레드
![](https://velog.velcdn.com/images/i-am-jiwon/post/e32834fb-da9d-44d7-be9e-0561a164bd99/image.png)

- 쓰레드는 프로세스 안에 포함되어 있다.
- 운영체제가 프로세스에게 code,data,stack,heap 영역을 할당해주고,쓰레드는 프로세스 안에서 stack을 제외한 다른 영역을 공유된다.
- 프로세스는 다른 프로세스와 정보 공유를 위해 IPC와 같은 과정이 필요하지만 쓰레드는 기본적으로 자원을 공유한다.

### 멀티 프로세스 vs 멀티 쓰레드
**멀티 프로세스**
하나의 응용프로그램을 여러개의 프로세스로 구성하여 각 프로세스가 하나의 작업을 처리하도로 하는 방식

- 장점 : 자식 프로세스에 문제가 생겨도 다른 자식에게 영향이 없다.
- 단점 : 
1. Context Switching에서 자원이 공유 되어있지 않기에 오버헤드(추가적으로 시간,메모리,자원이 사용되는 현상) 발생
2. 복잡한 IPC: 프로세스는 독립된 영역을 할당 받았기에 변수를 공유할 수 없다.

**멀티 쓰레드**
하나의 응용프로그램을 여러 개의 쓰레드로 구성하여 하나의 작업을 처리하는 방식

- 장점 :
1. 시스템 자원 소모 감소 : 프로세스 생성보다 자원 할당이 적다.
2. 처리 비용 감소 : 쓰레드는 Context Switching이 빠르다
3. 응답시간 단축 : stack을 제외한 메모리 영역을 공유하기에 응답이 빠르다.
- 단점 :
1. 디버깅이 까다롭고, 주의 깊은 설계 필요
2. 단일 프로세스 시스템은 효과가 없다.
3. 동기화 문제
4. 하나의 쓰레드 문제는 전체가 영향을 받는다.

> 쓰레드를 이용하는게 효율적이기 때문에 대부분의 경우 멀티 쓰레드를 사용한다.
