## 쿠키와 세션을 왜 사용할까?

클라이언트가 요청을 보내면 서버는 요청을 처리하여 응답을 한다. 이때 브라우저와 서버 간에 데이터를 주고받기 위한 방식으로 HTTP 프로토콜을 사용한다.

HTTP 프로토콜은 서버에 연결하고 요청하여 응답을 받으면 연결을 끊어버리는 Connectionless와 통신이 끝나면 상태를 유지하지 않는 Stateless 한 특징을 가진다. 이러한 특성을 보완하기 위해 쿠키와 세션을 사용한다.

## 쿠키(Cookie)

- 쿠키는 클라이언트(브라우저) 로컬에 저장되는 Key:Value 형태로 저장되는 데이터 파일로 쿠키 이름, 유효시간, 도메인 등으로 구성된다.
- 쿠키는 클라이언트의 상태 정보를 로컬에 저장했다가 참조한다. 
- setMaxAge()로 유효한 시간을 명시할 수 있으며, 유효시간이 정해지면 브라우저가 종료되어도 인증이 유지된다는 특징이 있다.
- Response Header의 Set-Cookie 속성을 사용하면 클라이언트에 쿠키를 만들 수 있고 사용자가 따로 요청하지 않아도 브라우저가 서버와 연결되었을 때 브라우저에서 자동적으로 쿠키를 생성하고, 응답할 때 쿠키를 담아서 보낸다.
- 쿠키 사용 예시로 쇼핑몰의 장바구니 기능, 자동 로그인 등이 있다.

### 쿠키의 동작 방식

1. 클라이언트가 페이지를 요청
2. 서버에서 쿠키를 생성하여 HTTP 헤더에 포함하여 응답
3. 브라우저가 종료되어도 쿠키 만료 기간이 있다면 클라이언트가 보관
4. 같은 요청일 경우 HTTP 헤더에 쿠키를 함께 보냄
5. 서버에서 쿠키를 읽어 이전 상태를 변경할 필요가 있을 때 쿠키를 업데이트하여 HTTP 헤더에 포함시켜 응답

## 세션(Session)

- 세션은 쿠키를 기반으로 하고 있지만, 사용자 정보 파일을 브라우저에 저장하는 쿠키와 달리 세션은 서버 측에서 저장하고 관리한다. 
- 서버에서는 클라이언트를 구분하기 위해 유일한 값인 세션 ID를 부여하며 웹 브라우저가 서버에 접속해서 브라우저를 종료할 때까지 인증 상태를 유지한다.
    - 클라이언트는 세션 ID를 쿠키를 통해 기억한다.
    - 이후 클라이언트가 요청을 보낼 때마다 헤더의 쿠키에 세션 ID를 담아서 전송한다.
- 서버는 클라이언트가 보낸 요청의 쿠키에 담긴 세션 ID와 세션 스토리지에 담긴 세션 ID를 대조해 인증을 판단한다.

### 세션의 동작 방식

1. 클라이언트가 서버 접속 시 세션 ID를 발급받고 쿠키를 사용해 저장
2. 클라이언트가 서버에 요청 시 쿠키의 세션 ID를 같이 전달
3. 서버는 세션 ID를 받아 클라이언트 정보로 사용
4. 서버 요청 처리 후 클라이언트에게 응답

> 왜 쿠키와 세션 둘다 사용할까?
 
 세션은 보안성이 좋지만 서버에 저장되고, 서버 자원은 한계가 있기 때문에 메모리 문제가 발생할 수 있다.

## 토큰

- 인증을 위해 사용되는 암호화된 접근 권한
- 사용자가 인증에 성공 시 서버는 토큰을 생성하여 클라이언트에게 보낸다.
- JWT(Json Web Token)은 인증에 필요한 정보를 암호화한 토큰으로 HTTP 헤더에 실어 서버에 전송한다.
- 세션 인증에서는 서버가 세션 ID를 저장하고 있다가 클라이언트가 쿠키에 실어 보낸 세션 ID와 대조해서 확인하는 반면, 토큰은 요청받은 서버가 토큰이 유효한지를 확인만 한다.
- 세션과 쿠키는 별도의 저장소가 필요하지만 JWT는 발급 후 검증만 하기 때문에 추가로 저장소가 필요하지 않다.

## 캐시

- 자주 사용되는 데이터나 값을 미리 복사해 놓는 임시 장소로 저장 공간이 작고 비용이 비싼 대신 빠른 성능을 제공한다.
- 접근 시간에 비해 원래 데이터를 접근하는 시간이 오래 걸리는 경우, 반복적으로 동일한 결과를 돌려주는 경우 캐시를 고려한다.
- 캐시 유효 시간이 초과하면, 서버를 통해 다시 데이터를 조회하고 캐시를 갱신한다.
- Local Cache
  - Local 장비 내에서만 사용되는 Cache로 Local 장비의 리소스를 이용한다.
  - Local에서만 작동하기 때문에 속도가 빠르다.
  - 다른 서버와 데이터 공유가 어렵다.
- Global Cache
  - 여러 서버에서 Cache 서버에 접근하여 사용하는 Cache로 분산된 서버에서 데이터를 저장하고 조회할 수 있다.
  - 네트워크를 통해 데이터를 가져오므로, Local Cache에 비해 상대적으로 느리다.
  - 별도의 Cache 서버를 이용하기 때문에 서버 간의 데이터 공유가 쉽다.
  
<br>

참고

[우아한Tech 쿠키 vs 세션 vs 토큰 vs 캐시](https://www.youtube.com/watch?v=gA1KsJ2ak10)
