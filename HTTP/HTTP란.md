## HTTP(Hypertext Protocol)

**HTTP**란 **서버와 클라이언트간의 메세지 교환 프로토콜**을 의미한다.

클라이언트가 리소스를 HTTP를 통해 요청하면 TCP, IP 프로토콜을 걸쳐 서버쪽의 HTTP까지 요청이 도달한다. 이에 대한 응답을 다시 서버에서 HTTP로 보내면 TCP, IP 프로토콜을 통과해 클라이언트까지 응답이 도달하게 된다.

## HTTP 프로토콜 구성

![img2](https://github.com/dilmah0203/TIL/blob/main/Image/HTTP.png)

## HTTP 프로토콜 특징

1. **클라이언트-서버 구조**

- Request Response 구조
- 클라이언트는 서버에 요청을 보내고, 응답을 대기
- 서버가 요청에 대한 결과를 만들어서 응답

2. **Stateless(무상태)**

- 서버가 클라이언트의 상태를 보존하지 않는다.
- 장점 : 서버 확장성 높음(Scale-Out)
- 단점 : 클라이언트가 추가 데이터 전송

상태가 유지되려면 항상 같은 서버가 유지되어야 한다. 하지만 무상태의 경우 상태를 보관하지 않기 때문에 아무 서버나 호출해도 된다. 중간에 서버가 장애났을 경우 다른 서버로 교체만 해주면 되기 때문이다. 

3. **Connectionless(비연결성)**

클라이언트가 서버에 요청을 보내고 응답을 받게되면 바로 클라이언트와 서버의 연결을 끊어버린다. 따라서 서버는 최소한의 자원만을 사용하게 되기 때문에 효율적이다.

TCP/IP 연결을 새로 맺어야 하는 한계가 있지만, 지금은 HTTP 지속 연결로 해결되었다.

## HTTP Method의 종류

- GET : 리소스 조회
- POST : 요청 데이터 처리, 주로 리소스 등록에 사용
- PUT : 리소스 수정, 해당 리소스가 없으면 생성(데이터를 덮어쓴다)
- PATCH : 리소스 일부 수정
- DELETE : 리소스 삭제

## HTTP Method의 속성

1. **안전**

- 호출해도 리소스를 변경하지 않는 메소드들을 safe하다고 한다.
- GET, HEAD 등이 있다.

2. **멱등**

- 여러번 요청을 수행해도 결과가 같음을 의미한다.
- GET, PUT, DELETE가 멱동성이 보장된다.

왜 중요할까?

**서버의 상태가 같음을 보장한다.** 대용량 트래픽의 경우 서버가 불안정 할 시에 멱등성이 중요하다.

3. **캐시가능**

- 향후 재사용을 위해 이에 대한 응답을 저장할 수 있음을 나타낸다.
- GET, POST, PATCH, HEAD가 캐시가능하다.
- POST, PATCH는 구현이 쉽지 않기 때문에 실제로는 GET, HEAD정도만 캐시를 사용한다.

## HTTP Method 활용

클라이언트에서 서버로 데이터를 전송할 때, 데이터 전달 방식은 크게 2가지가 있다.

- **쿼리 파라미터를 통한 데이터 전송**
  - GET, 주로 정렬 필터(검색어)
- **메세지 바디를 통한 데이터 전송**
  - POST, PUT, PATCH
  - 회원 가입, 상품 주문, 리소스 등록, 리소스 변경

```HTTP
GET /static/star.jpg HTTP/1.1
Host: localhost:8080
```

- 이미지, 정적 텍스트 문서
- 조회는 GET 사용
- 정적 데이터는 일반적으로 쿼리 파라미터 없이 리소스 경로로 단순 조회 가능

```HTTP
GET /search?q=hello&hl=ko HTTP/1.1
Host: www.google.com
```

- 주로 검색, 게시판 목록에서 정렬 필터(검색어)
- 조회는 GET 사용
- 쿼리 파라미터를 기반으로 정렬 필터해서 결과를 동적으로 생성

```HTTP
POST /members HTTP/1.1
Content-Type: application/json

{
  "username": "young",
  "age": 20
}
```

- POST, PUT, PATCH는 메세지 바디를 통해 데이터를 전송한다.
- Content-Type: application/json을 주로 사용
- 클라이언트는 등록될 리소스의 URI를 모른다.
- 서버가 새로 등록된 리소스 URI를 생성해준다.[(POST vs PUT)](https://github.com/dilmah0203/TIL/blob/main/HTTP/POST%20vs%20PUT%2C%20PATCH%20vs%20PUT.md?plain=1)
  - HTTP/1.1 201 Created
  - Location: **/members/100**
- 서버가 리소스의 URI를 생성하고 관리

```HTTP
PUT /members/100 HTTP/1.1
Content-Type: application/json

{
  "username": "hello",
  "age": 20
}
```

- 클라이언트가 리소스 URI를 알고 있어야 한다.


