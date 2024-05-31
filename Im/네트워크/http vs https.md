# HTTP (Hyper Text Transfer Protocol)
텍스트 기반의 통신규약으로 인터넷에서 데이터를 주고받을 수 있는 프로토콜
클라이언트가 요청을하면 서버가 응답을 하는 형태로 동작한다.

#### 특징
- HTTP 메시지는 HTTP 서버와 HTTP 클라이언트에 의해 해석됨
- TCP/IP를 이용하는 응용 프로토콜
- 비연결성 프로토콜이다. ( Cookie와 Session 등장의 이유 )
- 요청/응답 방식으로 동작

#### 일반적인 HTTP요청과 응답
**요청**
Http 요청은 HTTP 프로토콜을 따르는 일련의 텍스트다.
Get 요청 예시)

![](https://velog.velcdn.com/images/i-am-jiwon/post/9ee90fd7-c1d3-41c2-830a-03f4aa178cd9/image.png)

**응답**
서버는 HTTP 요청을 받으면 요청과 유사한 응답을 보낸다.
응답 예시)

![](https://velog.velcdn.com/images/i-am-jiwon/post/a44d85c1-7310-479d-9869-06285378590b/image.png)

> 출처 : [링크텍스트](https://www.cloudflare.com/ko-kr/learning/ssl/why-is-http-not-secure/)

이 요청과 응답은 사용자가 아니라도 누구든 읽을 수 있다.
이것은 중요한 정보를 다루기에는 적합하지 않다.

# HTTPS(Hypertext Transfer Protocol Secure)
HTTP에 보안을 뜻하는 Secure이 추가된 프로토콜이다.
보안을 위해서 HTTPS는 SSL(Secure Socket Layer)나 TLS(Transport Layer Security Protocol)을 사용하여 데이터를 보호한다.

## SSL/TLS
TLS는 SSL에서 발전하며 이름이 변경 되었는데 SSL이라는 명칭으로 계속 사용되기도 하며 SSL/TLS로 합쳐서 부르기도 한다.

### **작동 방식**
SSL 프로토콜은 SSL 인증서를 사용해 작동한다.

1. SSL 인증서에는 서비스 정보, 서버키가 들어있고 CA(Certificate Authority, 공개키를 저장해주는 신뢰성이 검증된 민간 기업)에 의해 암호화 된다.

2. 브라우저는 내부적으로 CA리스트를 갖고 있고 각 CA의 공개키를 갖고 있다.
서버는 클라이언트에게 인증서를 제공하고 자신이 갖고있는 CA리스트에 있는 지 확인후 해당 공개키를 이용해 복호화 한다.

3. 복호화가 성공했다면 CA의 비공개키로 암호화 된 것이기 때문에 보안성 검증 완료

4. 신뢰할 수 있으므로 TLS/SSL Handshake를 통해 세션키를 생성하고 통신을 시작



#### **암호화 방식**
- 공개키 방식
![](https://velog.velcdn.com/images/i-am-jiwon/post/2006f912-c438-4d33-a99d-8ada62002b5e/image.png)

공개키, 개인키를 한쌍으로 각각 암호화/복호화에 사용한다.
일반적으로 공개키로 암호화 한 것을 개인키로 복호화 하는데, 개인키를 먼저 만들고 공개키를 만들기 때문에
같은 쌍이 아니면 암호화 복호화가 불가능하다.
비대칭키라고 불림

장점 : 키 분배가 필요 없다.
단점 : 속도가 느리다.
대표 알고리즘 : 디피-헬만, RSA

- 대칭키 방식
![](https://velog.velcdn.com/images/i-am-jiwon/post/f153a7e5-12bb-4ae6-9391-64bbe497ab67/image.png)

하나의 키를 통해 암호화와 복호화를 진행한다.
하나의 키를 클라이언트와 서버가 같이 사용한다.

장점 : 속도가 빠르다.
단점 : 보안이 약하다.
대표 알고리즘 : SEED, DES, 3DES, AES, ARIA

#### **TLS/SSL Handshake**
![](https://velog.velcdn.com/images/i-am-jiwon/post/e6866d21-cabd-4b88-b7fb-e93de805fdab/image.png)

1. 클라이언트가 서버에 접속해 말을 건다. (client hello)
아래의 정보를 서버에 보낸다.
- 브라우저의 SSL/TLS 버전
- 지원하는 암호화 방식 모음
- 임의의 난수
- 이전에 handshake를 했다면 그때의 세션 id
- 기타 확장 정보

2. 응답 및 정보 제공 (server hello)
- 브라우저의 방식중 서버가 선택한 암호화 방식
- 서버의 공개키가 담긴 SSL인증서(CA의 비밀키로 암호화 된 상태)
- 서버가 생성한 난수

3. 서버의 SSL 인증서 확인
브라우저에 내장 된 CA공개키로 복호화 하고 성공한다면 성공

4. 브라우저는 자신의 난수와 서버의 난수를 사용해 premaster secret 만들기
웹 서버 인증서에 포함된 서버 공개키로 암호화하여 전송한다.

5. 서버는 자신의 비밀키로 브라우저의 premaster secret 복호화
복호화 한 값을 master secret으로 저장 후 Session key생성
세션키는 대칭키 암호화에 사용. 이것으로 데이터를 암호화, 복호화 한다.

6. HTTPS 통신 시작

## HTTPS 장단점
장점
- 웹사이트의 무결성을 보호해준다.
- 검색엔진최적화(SEO)에서 키워드 검색시 상위 노출되는 기준이다.

단점
- 녹음, 위치 등 사용자의 명시적 권한 허락 필요
- HTTP에 비해 느리다.
