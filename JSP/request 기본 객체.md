# 💡 **request 기본 객체**

request 기본 객체는 웹 브라우저의 요청과 관련이 있다. 웹 브라우저에
웹 사이트의 주소를 입력하면, 웹 브라우저는 해당 웹 서버에 연결한 후
요청 정보를 전송하는데, 이 요청 정보를 제공하는 것이 request 기본 객체이다.

request 기본 객체가 제공하는 기능은 다음과 같다.

- 클라이언트 정보 및 서버 정보 읽기

  - getRemoteAddr() : 웹 서버에 연결한 클라이언트의 IP 주소를 구한다.

  - getContentLength() : 클라이언트가 전송한 요청 정보의 길이를 구한다.

  - getCharacterEncoding() : 클라이언트가 요청 정보를 전송할 때 사용한 캐릭터의 인코딩을 구한다.

  - getContentType() : 클라이언트가 요청 정보를 전송할 때 사용한 컨텐츠의 타입을 구한다.

  - getProtocol() : 클라이언트가 요청한 프로토콜을 구한다.

  - getMethod() : 웹 브라우저가 정보 전송 시 사용한 방식을 구한다.

  - getRequestURI() : URL에서 경로를 구한다.

  - getContextPath() : JSP 페이지가 속한 웹 어플리케이션의 컨텍스트 경로를 구한다.

  - getServerName() : 연결할 때 사용한 서버 이름을 구한다.

  - getServerPort() : 서버가 실행중인 포트 번호를 구한다.

<br>

웹 브라우저가 전송한 파라미터를 읽어올 수 있는 메소드를 제공한다.

- 요청 파라미터 처리

  - getParameter(String name) : 이름이 name인 파라미터의 값을 구한다.

  - getParameterValues(String name) : 이름이 name인 파라미터의 모든 값을 배열로 구한다.

  - getParameterNames() : 웹 브라우저가 전송한 파라미터의 이름 목록을 구한다.

  - getParameterMap() : 웹 브라우저가 전송한 파라미터의 맵<파라미터 이름,값> 쌍을 구한다.

<br>

HTTP 프로토콜은 헤더 정보에 부가적인 정보를 담도록 하고 있다. request 기본 객체는 이러한 헤더 정보를 읽어올 수 있는 기능을 제공한다.

- 요청 헤더 정보의 처리

  - getHeader(String name) : 지정한 이름의 헤더 값을 구한다.

  - getHeaders(String name) : 헤더 목록을 구한다.

  - getHeaderNames() : 모든 헤더의 이름을 구한다.

  - getIntHeader(String name) : 헤더의 값을 정수 값으로 읽어온다.

  - getDateHeader(String name) : 헤더의 값을 시간 값으로 읽어온다.
