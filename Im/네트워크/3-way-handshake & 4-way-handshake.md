
# 3-Way-Handshake
TCP/IP 프로토콜을 이용해서 통신하는 응용프로그램은 데이터를 주고받기 전에 먼저 연결을 진행한다.
3-Way Handshake는 이 연결 과정을 의미한다.

#### TCP란
TCP (Transmission Control Protocol)
인터넷에서 데이터를 메세지 형식으로 보내기 위해 IP와 함께 사용하는 프로토콜이다.
TCP는 패킷의 추적 및 관리 / IP는 배달을 하게된다.

**TCP 특징**
- 3-way handshaking과정을 통해 연결을 설정하고 4-way handshaking을 통해 해제한다.
- 흐름 제어 및 혼잡 제어.
- 높은 신뢰성을 보장한다.
- UDP보다 속도가 느리다.
- 전이중(Full-Duplex), 점대점(Point to Point) 방식.

---


# 3-Way-Handshake 에서 사용되는 TCP 헤더 필드

![](https://velog.velcdn.com/images/i-am-jiwon/post/5ed4f3b6-d26a-40b6-8f59-b32cdebf633d/image.png)


**- Sequence Number**
- Segment에 있는 첫번째 바이트의 바이트 스트림 번호이다.
ex) 0 ~ 999 > 0 / 1000 ~ 1999 > 1000
- TCP 종료시에는 임의의 랜덤값으로 설정해야 노출이 되지 않는다.

**- Acknowledgement Number**
- 받고 싶은 다음 바이트의 번호
ex) 0 ~ 999를 받았으면 ack# = 1000

**- Control bits**
- ACK
	- acknowledgment '승인'의 약자.
	- 패킷을 받았다는 응답을 할 때 사용한다.
	- Acknowledgement Number가 유효한지를 나타낸다.
	- 최초 연결의 첫 번째 세그먼트를 제외한 모든 Segment의 ACK 비트는 1로 설정한다. (최초는 응답할 요청이 없기 때문)
- SYN
	- synchronize '동시에 발생하다'의 약자.
	- 연결을 요청할 때 SYN bit를 사용한다.
	- 연결을 요청하는 경우 1로 설정한다. SYN bit=1 이면 TCP 연결 요청하는 과정이다.
	- 다른 모든 경우는 0으로 설정한다.

---

# 3-Way-Handshake 과정
_**일반적으로 클라이언트 / 서버 둘 다 먼저 요청 할 수 있기 때문에 먼저 요청 한 쪽을 클라이언트 받은 사람을 서버라고 칭함.**_

![](https://velog.velcdn.com/images/i-am-jiwon/post/fee1c42e-aa2d-4cf5-84da-cd5658120853/image.png)


**1. 클라이언드 ---- (SYN) ---- > 서버**
클라이언트가 서버에게 연결을 요청하는 SYN segment를 보낸다.
- Segment Header의 SYN bit를 1로 설정
- PORT
Client : CLOSE - SYN_SENT로 변경
SERVER : LISTEN


**2. 클라이언트 < ---- (ACK + SYN) ---- 서버**
1. 서버가 클라이언트의 SYN segment에 대한 ACK segment 전송
2. 동시에 서버가 클라이언트에게 연결을 요청하는 SYN segment를 전송 (SYN bit을 1로 설정)
3. SYN/ACK 를 전송하고 SYN RCVD(Received)의 상태로 클라이언트의 ACK 기다린다.
4. 클라이언트는 ACK segment를 받고 연결이 완료 된 ESTAB 상태가 된다.


**3. 클라이언트 ---- (ACK) ---- > 서버**
클라이언트는 서버의 SYN에 대하여 ACK를 전송한다.
- 연결 요청이 아니므로 SYN bit는 0

서버는 ACK를 받고 ESTAB가 된다.

---

# 4-Way-Handshake 과정

![](https://velog.velcdn.com/images/i-am-jiwon/post/c5bdc492-9250-418d-9ddb-93b1e038cd0d/image.png)


4-Way Handshake은 연결을 해제 (Connecntion Termination)하는 과정이다. 
FIN 플래그(세션을 종료시키는데 사용되며, 더 이상 보낸 데이터가 없음을 의미)를 사용한다.

**1. 클라이언드 ---- (FIN) ---- > 서버**
클라이언트가 연결을 종료하겠다는 FIN플래그를 전송한다.
- FIN패킷에는 실질적으로 ACK도 포함되어있다.

**2. 클라이언트 < ---- (ACK) ---- 서버**
서버는 FIN을 받고 확인했단는 ACK를 보내고 자신의 통신이 끝날 때 까지 기다린다 (TIME_WAIT 상태)


**3. 클라이언트 < ---- (FIN) ---- 서버**
데이터를 모두 보냈다면 FIN을 클라이언트에게 보낸 후 승인을 기다리는 LAST_ACK상태로 들어감

**4. 클라이언드 ---- (ACK) ---- > 서버**
클라이트는 FIN을 받고 ACK를 보낸다.
뒤늦게 도착하는 패킷을 대비하기 위해 클라언트는 일정시간을(디폴트 240초)기다린 후 소켓을 닫는다. < (TIME_WAIT)
