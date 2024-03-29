## 로드밸런서(Load Balancer)란?

**다수의 사용자가 서버에 접근할 때 해결방법**

- Scale-up : 단일 서버의 하드웨어를 고성능으로 바꾼다.
    - 한계가 있다.
- Scale-out : 다수의 서버를 사용해 처리를 분담한다.
    - 이 때, 클라이언트의 요청에 일관성 있게 응답하기 위해 필요한 것이 로드밸런서이다.
    - **로드밸런서**는 트래픽을 여러 대의 서버로 분산해주며, 일부 서버에 트래픽이 몰리지 않도록 요청을 중개한다.

## 프록시(Proxy) 란?

- 프록시 : 서버와 클라이언트 간의 중계 서버로서 통신을 대신 수행하는 역할
- 프록시 서버는 클라이언트의 대리 역할을 하거나 서버의 대리 역할을 할 수 있다.

## 포워드 프록시(Forward Proxy)

![img](https://github.com/dilmah0203/TIL/blob/main/Image/Forward%20Proxy.PNG)

- 클라이언트와 인터넷 사이에 위치
- 클라이언트 대신 서버에 요청을 보낸다.
- 클라이언트는 내부 서버에 대한 정보를 알 필요 없이 포워드 프록시에만 요청하면 된다.

예를들어 클라이언트가 `naver.com`을 요청하면 포워드 프록시 서버는 `naver.com` 리소스를 대신 받아와 클라이언트에게 전달한다. 이 경우 서버에서 받는 IP는 클라이언트의 IP가 아닌 프록시 서버의 IP이기 때문에 서버는 클라이언트가 누군지 알 수 없다. 즉 **서버에게 클라이언트가 누구인지 감춰주는 역할**을 한다.

- 특징
    - 캐싱 : 웹 페이지에 접근하면 프록시 서버는 해당 페이지 서버의 정보를 캐싱(임시보관)해둔다. 이후 해당 페이지에 접근하거나 다른 클라이언트가 해당 페이지를 요청할 때 캐싱된 정보를 그대로 반환하여 서버의 부하를 줄일 수 있다.
    - 보안 : 클라이언트가 서버에 직접 접근하는 것을 방지하기 때문에 접근 가능한 사이트를 제한할 수 있다.
    
## 리버스 프록시(Reverse Proxy)

![img2](https://github.com/dilmah0203/TIL/blob/main/Image/Reverse%20Proxy.PNG)

- 인터넷과 서버 사이에 위치
- 서버 대신 클라이언트에 응답을 보낸다.

예를들어 클라이언트가 `naver.com`에 데이터 요청을 하면 리버스 프록시가 요청을 받아서 서버로 요청을 전달하고 응답을 받아 클라이언트에게 보낸다. 이 경우 클라이언트는 서버를 직접 호출하는 것이 아니라 프록시 서버를 통해 호출하기 때문에 리버스 프록시는 **서버를 감추는 역할**을 하게된다.

- 특징
    - 로드밸런싱 : 리버스 프록시 서버 뒤에 여러 서버를 두어 사용자의 요청을 분산할 수 있다. 
    - 보안 : 리버스 프록시를 사용하면 서버 측 보안에 좋다. 리버스 프록시를 사용하면 서버의 IP 주소를 노출시키지 않을 수 있다. 클라이언트가 인터넷을 통해 리버스 프록시 서버 url에 요청을 하면 리버스 프록시는 서버에게 요청을 경유해서 보내게 된다. 이렇게 되면 클라이언트는 서버의 url을 모른채 리버스 프록시 url을 통해 서비스를 이용하게 되고, 이는 즉 서버의 정보를 숨기는 효과가 된다.
    - 캐싱 : 포워드 프록시의 캐싱과 비슷한 기능

> 왜 프록시를 사용할까?

1. 필터 : 부적절한 사이트의 접근을 거부한다.
2. 접근 제어 : 허가된 클라이언트만 접근할 수 있도록 허용한다.
3. 캐싱 : 요청을 관리하고, 해당 요청이 오면 서버까지 거치지 않고 바로 프록시에서 응답한다.

