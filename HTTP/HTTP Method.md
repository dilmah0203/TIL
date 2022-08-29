## HTTP Method

### HTTP Method의 종류와 특징

- GET : 데이터 조회

- POST : 데이터 전송

- PUT : 데이터 전체 수정, 해당 리소스가 없으면 생성(데이터를 덮어쓴다)

- PATCH : 데이터 일부 수정

- DELETE : 데이터 삭제

### HTTP Method의 속성

1. **안전**

- 데이터를 수정하지 않는 메소드들을 safe하다고 한다.
- GET, HEAD 등이 있다.

2. **멱등**

- 여러번 요청을 수행해도 결과가 같음을 의미한다.
- GET, PUT, DELETE가 멱동성이 보장된다.

3. **캐시가능**

- 향후 재사용을 위해 이에 대한 응답을 저장할 수 있음을 나타낸다.
- GET, POST, PATCH, HEAD가 캐시가능하다.
- POST, PATCH는 구현이 쉽지 않기 때문에 실제로는 GET, HEAD정도만 캐시를 사용한다.