### 요약
> RESTful API는 REST스러운 API로 자원을 주고 받을 때 URI로 자원을 명시하고, HTTP Method를 이용해 자원을 CRUD한다.
따라서 RESTful API를 설계할 때 URI, HTTP Method 만으로도 어떤 자원으로 어떤 일을 하는지 알기 쉽게 설계하는 것이 중요하다. 

* 반성할 점: 본인은 REST API만들 때 대문자를 사용하였다. 
---
### REST란 - Representational State Transfer

**REST는 자원을 이름으로 구분해 해당 자원의 상태를 주고 받는 모든 것을 의미한다.**

구성 요소
- 자원 - 각 자원은 자신만의 URI를 통해 접근 할 수 있다. 
- 행위 - HTTP Method(GET, POST, PUT, DELETE)를 통해 어떤 방식으로 자원을 조작할지 표현한다.
- 표현 - 클라이언트가 서버에 HTTP Method로 자원에 접근하면 보내주는 자원의 상태(JSON, XML, ...)를 의미한다.

--- 
**특징**

1.클라이언트 - 서버 구조(Client - Server)

2.무상태(Stateless)
- 서버가 클라이언트의 정보를 저장하지 않는다.

3.캐시 처리 기능(Cacheable)

4.계층 구조(Layered System)

5.인터페이스 일관성(Uniform Interface)

6.자체 표현 구조(Self-descriptiveness)


---
### REST API? - REST의 특성을 지닌 API

>API: 어플리케이션 간 통신할 때 사용하는 규칙 모음

**설계 규칙**
- URI는 자원의 정보를 표시해야 한다.
- 자원에 대한 행위는 HTTP Method(GET, PUT, POST, DELETE) 로 표현한다.
- 슬래시 구분자(/)는 계층 관계를 나타내는데 사용한다.
- URI 마지막 문자로 슬래시를 포함하지 않는다
- 하이픈(-) 은 URI 가독성을 높이는데 사용
- 밑줄(_)은 사용하지 않는다.
- URI 경로에는 소문자가 적합
- 파일 확장자는 URI에 포함하지 않는다.
