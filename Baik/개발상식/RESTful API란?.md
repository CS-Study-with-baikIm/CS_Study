# REST API 란?

REST API 에서 REST는 Representational State Transfer 의 약자로 소프트웨어 프로그램 아키텍처의 한 형식 입니다.

즉, 자원을 이름 (자원의 표현) 으로 구분하여 해당 자원의 상태 (정보)를 주고 받는 모든 것을 의미한다.

월드 와이드 웹 (WWW) 과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 개발 아키텍처의 한 형식

REST는 기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다.

## Rest 란?
HTTP URI를 통해 자원을 명시하고, HTTP Method를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.

#### CRUD OPERATION
- Create(Post) : 생성 
- Read(Get) : 조회
- Update(Put) : 수정
- Delete : 삭제
- HEAD 

## REST의 장점

- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.

- 서버와 클라이언트의 역할을 분리해준다.

 - 서버와 클라이언트가 각각 독립적으로 존재하여 서로에게 영향을 끼치지 않는다.

## REST의 단점

- 표준이 존재하지 않는다.

- HTTP Method 형태가 제한적이다.

## Rest의 필요성

다양한 클라이언트와 브라우저 등 서버가 필요한 환경이 다양해 지면서
서버와 클라이언트 분리의 필요성을 느끼게 됨.


## REST 구성 요소

#### 자원(Resource): URI

1. 모든 자원에 고유한 ID가 존재하고, 이 자원은 Server에 존재한다.

2. 자원을 구별하는 ID는 ‘/groups/:group_id’와 같은 HTTP URI 다.

3. Client는 URI를 이용해서 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청한다.

#### 행위(Verb): HTTP Method

1. HTTP 프로토콜의 Method를 사용한다.

2. HTTP 프로토콜은 GET, POST, PUT, DELETE 와 같은 메서드를 제공한다.

#### 표현(Representation of Resource)

1. Client가 자원의 상태(정보)에 대한 조작을 요청하면 Server는 이에 적절한 응답(Representation)을 보낸다.

2. REST에서 하나의 자원은 JSON, XML, TEXT, RSS 등 여러 형태의 Representation으로 나타내어 질 수 있다.
3. JSON 혹은 XML를 통해 데이터를 주고 받는 것이 일반적이다.


## REST 특징
#### Server-Client(서버-클라이언트 구조)

- 자원이 있는 쪽이 Server, 자원을 요청하는 쪽이 Client가 된다.
  -  REST Server: API를 제공하고 비즈니스 로직 처리 및 저장을 책임진다.
  - Client: 사용자 인증이나 context(세션, 로그인 정보) 등을 직접 관리하고 책임진다.
- 서로 간 의존성이 줄어든다.

#### Stateless(무상태)

- HTTP 프로토콜은 Stateless Protocol이므로 REST 역시 무상태성을 갖는다.
- Client의 context를 Server에 저장하지 않는다.
  - 세션과 쿠키와 같은 context 정보를 신경쓰지 않아도 되므로 구현이 단순해진다.
- Server는 각각의 요청을 완전히 별개의 것으로 인식하고 처리한다.
  - 각 API 서버는 Client의 요청만을 단순 처리한다.
  - 이전 요청이 다음 요청의 처리에 연관되어서는 안된다.
  - 물론 이전 요청이 DB를 수정하여 DB에 의해 바뀌는 것은 허용한다.
  - Server의 처리 방식에 일관성을 부여하고 부담이 줄어들며, 서비스의 자유도가 높아진다.



#### Cacheable(캐시 처리 가능)

- 웹 표준 HTTP 프로토콜을 그대로 사용하므로 웹에서 사용하는 기존의 인프라를 그대로 활용할 수 있다.
  - 즉, HTTP가 가진 가장 강력한 특징 중 하나인 캐싱 기능을 적용할 수 있다.
  - HTTP 프로토콜 표준에서 사용하는 Last-Modified 태그나 E-Tag를 이용하면 캐싱 구현이 가능하다.
- 대량의 요청을 효율적으로 처리하기 위해 캐시가 요구된다.
- 캐시 사용을 통해 응답시간이 빨라지고 REST Server 트랜잭션이 발생하지 않기 때문에 전체 응답시간, 성능, 서버의 자원 이용률을 향상시킬 수 있다.

#### Layered System(계층화)

- Client는 REST API Server만 호출한다.
- REST Server는 다중 계층으로 구성될 수 있다.
  - API Server는 순수 비즈니스 로직을 수행하고 그 앞단에 보안, 로드밸런싱, 암호화, 사용자 인증 등을 추가하여 구조상의 유연성을 줄 수 있다.
또한 로드밸런싱, 공유 캐시 등을 통해 확장성과 보안성을 향상시킬 수 있다.
- PROXY, 게이트웨이 같은 네트워크 기반의 중간 매체를 사용할 수 있다.

#### Code-On-Demand(optional)

- Server로부터 스크립트를 받아서 Client에서 실행한다.
- 반드시 충족할 필요는 없다.



## REST API란

### API(Application Programming Interface)란

데이터와 기능의 집합을 제공하여 컴퓨터 프로그램간 상호작용을 촉진하며, 서로 정보를 교환가능 하도록 하는 것

## RESTful
### RESTful이란

- RESTful은 일반적으로 REST라는 아키텍처를 구현하는 웹 서비스를 나타내기 위해 사용되는 용어이다.

- ‘REST API’를 제공하는 웹 서비스를 ‘RESTful’하다고 할 수 있다.

- 즉, REST 원리를 따르는 시스템은 RESTful이란 용어로 지칭된다.



### RESTful의 목적

- 이해하기 쉽고 사용하기 쉬운 REST API를 만드는 것
- RESTful한 API를 구현하는 근본적인 목적이 성능 향상에 있는 것이 아니라 일관적인 컨벤션을 통한 API의 이해도 및 호환성을 높이는 것이 주 동기이니, 성능이 중요한 상황에서는 굳이 RESTful한 API를 구현할 필요는 없다.
- RESTful 하지 못한 경우
  
  ex1) CRUD 기능을 모두 POST로만 처리하는 API

  ex2) route에 resource, id 외의 정보가 들어가는 경우(/students/updateName)

