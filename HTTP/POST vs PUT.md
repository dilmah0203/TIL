## **POST vs PUT**

### **멱등성(Idempotence)이란?**

여러번 수행해도 결과가 같음을 의미한다 

### **POST**

리소스 결정권이 클라이언트가 아닌 서버가 가지고 있다

- POST Request는 멱등하지 않다

  여러번의 재시도에 대한 모든 결과값이 동일하지 않다는 것이다. <br>
  즉, POST로 동일한 요청을 N번 보낸다면, N개의 다른 리소스들이 생성되는 것이다.

- POST Request의 Response는 Caching 가능 하다

### **PUT**

리소스의 위치를 명확히 알고 요청을 할 경우 사용

if resource 존재 -> Update(갱신) <br>
else -> Create(생성)

- PUT Request는 멱등하다

  PUT request로는 새로운 정보가 계속되서 생성되지 않는다. <br>
  여러번 재시도를 하더라도, 동일한 결과 값을 받는다.

- POST Request의 Response는 Caching 할 수 없다
