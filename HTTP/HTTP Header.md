## HTTP Header

- 헤더는 `field-name : field value`가 올 수 있다. field-name은 대소문자 구분이 없다. 
- 또한 HTTP 전송에 필요한 모든 부가정보(메세지 바디의 내용, 크기, 인증, 서버 정보, 캐시 관리 정보)를 담고 있다. 

![img](https://github.com/dilmah0203/TIL/blob/main/Image/HTTP%20Header.png)

- 메세지 본문(message body)를 통해 표현 데이터 전달
- **표현**은 요청이나 응답에서 전달할 실제 데이터
- **표현 헤더는 표현 데이터**를 해석할 수 있는 정보 제공
  - 데이터 유형(html, json), 데이터 길이, 압축 정보 등등

1. **표현**
- Content-Type : 표현 데이터의 형식
- Content-Length : 표현 데이터의 길이
- Content-Language : 표현 데이터의 자연 언어
- Content-Encoding : 표현 데이터의 압축 방식

표현 헤더는 전송, 응답 둘다 사용된다.

2. **협상**  : 클라이언트가 선호하는 표현 요청

```HTTP
GET /event
Accept-Language: ko-KR,ko;q=0.9,es-US;q=0.8,en;q=0.7
```

- Accept : 클라이언트가 선호하는 미디어 타입 전달
- Accept-Charset : 클라이언트가 선호하는 문자 인코딩
- Accept-Encoding : 클라이언트가 선호하는 압축 인코딩
- Accept-Language : 클라이언트가 선호하는 자연 언어

Quality Values(q)값을 사용하여 우선순위를 정할 수 있다. 0~1의 값으로 클수록 높은우선순위를 가진다. 협상 헤더는 요청시에만 사용한다.

3. **전송 방식**

- 단순 전송 : 요청에 대한 응답시 메세지 바디에 대한 Content-Length를 지정하는 전송 방식 

```HTTP
HTTP/1.1 200 OK
Content-Type: text/html;charset=UTF-8
Content-Length: 3423
```

- 압축 전송 : 서버에서 메시지 바디를 압축하여 용량을 감소시켜 전달하는 전송 방식으로 Content-Encoding이라는 항목을 헤더에 넣어 압축방식을 클라이언트에게 전달해주어야 한다.

```HTTP
HTTP/1.1 200 OK
Content-Type: text/html;charset=UTF-8
Content-Encoding: gzip
```

- 분할 전송 : 서버에서 클라이언트로 응답 메시지를 특정 단위로 쪼개서 보내는 전송 방법으로 Transfer-Encoding을 명시해주어야 한다. chunked라는 덩어리로 쪼개서 보낸다. 분할 전송때는 Content-Length를 넣으면 안된다.(길이를 예측할 수 없기 때문에)

```HTTP
HTTP/1.1 200 OK
Content-Type: text/plain
Transfer-Encoding: chunked
```

- 범위 전송 : 특정 범위를 지정해서 요청에 대한 응답을 받는 전송방법

```HTTP
HTTP/1.1 200 OK
Content-Type: text/plain
Content-Range: bytes 1001-2000 / 2000
```

요청과 응답 모두 사용될 수 있다.

4. **일반 정보**

-  Referer : 이전 웹 페이지의 주소, 요청에서 사용
-  User-Agent : 유저 에이전트 애플리케이션 정보(웹 브라우저 정보), 요청에서 사용
-  Server : 요청을 처리하는 ORIGIN 서버의 소프트웨어 정보를 말한다. 응답에서 사용
-  Date : 메세지가 발생한 날짜와 시간을 나타낸다. 응답에서 사용

5. **특별한 정보**

- Host : 요청한 호스트 정보(도메인)로 필수값이다. 요청에서 사용한다.
- Location : 페이지 리다이렉션시에 사용된다. 웹 브라우저는 3xx 응답 결과에 Location헤더가 있으면, Location 위치로 자동 이동한다.
- Allow : 허용 가능한 HTTP 메소드로 405에서 응답에 포함해야한다.

6. **인증**

- Authorization : 클라이언트 인증 정보를 서버에 전달
- www-Authenticate : 인증이 제대로 되지 않았을 때, 리소스 접근시 필요한 인증 방법 정의(401 Unauthorized 응답과 함께 사용)

7. **쿠키**

- Set-Cookie : 서버에서 클라이언트로 쿠키 전달(응답)
- Cookie : 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청시 서버로 전달

웹 브라우저에서 POST로 로그인을 하면 서버는 Set-Cookie 헤더를 만들어 응답한다. 브라우저는 내부의 쿠키 저장소에 쿠키 값을 저장하고 로그인 이후에 다른 페이지에 접근할 때마다 Cookie 헤더에 넣어 서버에 보낸다.

- Secure
  - 쿠키는 http, https를 구분하지 않고 전송
  - Secure를 적용하면 https인 경우에만 전송
- HttpOnly
  - XSS 공격 방지
- SameSite
  - 요청 도메인과 쿠키에 설정된 도메인이 같은 경우만 쿠키 전송

8. **캐시와 조건부 요청**

캐시 만료후에도 서버에서 데이터를 변경하지 않은 경우 서버에서 동일한 데이터를 요청해서 응답받는 것은 비용낭비다. 이럴때 저장해둔 캐시를 재사용할 수 있으면 좋은데, 어떻게 클라이언트의 데이터와 서버의 데이터가 동일하다는 것을 알 수 있을까? 그래서 **검증 헤더**가 들어가게 된다.

- 데이터가 마지막으로 수정된 시간정보를 헤더에 작성해준다. 
  - **Last-Modified: 2020년 11월 10일 10:00:00**
- 응답 결과를 캐시에 저장할 때 데이터 최종 수정일도 저장된다. 

![img](https://github.com/dilmah0203/TIL/blob/main/Image/HTTP_Header1.png)

- 캐시 시간이 초과해서 다시 요청을 할 경우, 캐시에 최종 수정일 정보(Last-Modified)가 있다면 요청 헤더 **if-modified-since**에 해당 날짜를 담아서 서버에 보낸다. 서버는 해당 자료의 최종 수정일과 비교해서 데이터가 수정이 안되었을 경우 응답 메세지에 이를 담아서 알려준다.

![img2](https://github.com/dilmah0203/TIL/blob/main/Image/HTTP_Header2.png)

- HTTP Body는 응답 데이터에 없다.
- 상태코드는 304 Not Modified로 변경된것이 없다는 것을 알린다.
- 그래서 전송 데이터는 바디가 빠졌기에 헤더만 포함된 0.1M만 전송된다.
- 클라이언트에서는 해당 응답을 받은 뒤 캐시를 갱신해주고 다시 일정시간 유효하게 된다.

![img3](https://github.com/dilmah0203/TIL/blob/main/Image/HTTP_Header3.png)

즉 캐시 유효 시간이 초과해도, 서버의 데이터가 갱신되지 않으면 304 Not Modified + 헤더 메타 정보만 응답한다. 클라이언트는 서버가 보낸 응답 정보로 캐시의 메타 정보를 갱신하고 재활용한다. 결과적으로 네트워크 다운로드가 발생하지만 용량이 적은 헤더만 다운로드받으면 된다.

- Cache-Control : 캐시 유효 시간을 설정한다. 지시어인 max-age는 초 단위로 설정할 수 있다. no-cache는 캐시해도 되지만 항상 origin 서버에 검증하고 사용한다. no-store는 데이터에 민감한 정보가 있으므로 저장하면 안된다.
