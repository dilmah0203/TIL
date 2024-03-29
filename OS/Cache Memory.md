## 캐시 메모리(Cache Memory)란?

캐시 메모리는 자주필요한 데이터나 계산된 결과 값의 복사본을 저장함으로써 처리 속도를 향상시킨다.

- CPU와 주기억장치(메인 메모리) 사이에 위치
- 속도가 빠른 장치와 느린 장치간의 속도 차에 따른 병목현상을 줄이기 위한 메모리
- 재사용 가능성이 높은 데이터 복사본을 저장해둔 후 CPU가 요청하는 데이터를 빠르게 전달

## 캐시의 동작 원리

### 캐시(Cache)의 지역성(Locality)

- **시간적 지역성** 
  - 특정 데이터가 한 번 접근되었을 경우, 가까운 시일 내에 또 한번 해당 데이터에 접근할 가능성이 높은 것
  - 메모리 상의 같은 주소에 여러 차례 읽기 쓰기를 수행할 경우 효율성을 높일 수 있다.

- **공간적 지역성** 
  - 특정 데이터와 가까운 주소가 순서대로 접근되었을 경우
  - 메모리 주소를 오름차순이나 내림차순으로 접근한다면 효율성을 높일 수 있다.

**지역성의 원리**에 따라 데이터를 예측하여 캐시 메모리에 미리 담아두고 캐시 메모리에 있는 데이터는 메인 메모리를 참조하지 않고 바로 가져와 실행한다.

## 캐시 히트(Hit)와 미스(Miss)

캐시 메모리가 해당 데이터를 가지고 있다면 캐시 히트, 해당 데이터가 없어서 메인 메모리에서 가져와야 한다면 캐시 미스라고 한다. 일반적으로 미스가 달성하면 캐싱을 한다.

데이터 변경 시 캐시 메모리와 메인 메모리에 데이터 저장 시점에 관한 정책은 두 가지가 있다.

1. **Write Through 정책**
- 캐시 메모리에 데이터가 Write될 때 메인 메모리도 바로 업데이트
- 캐시의 일관성을 유지할 수 있지만, 메인 메모리는 데이터 처리 속도가 느리기 때문에 CPU가 대기하는 시간이 늘어난다.

2. **Write Back 정책**
- 캐시 메모리에만 데이터를 Write한다. 
- 캐시 메모리가 새로운 데이터로 교체될 때 데이터를 메인 메모리에도 업데이트
- Write 동작을 최소화 하여 성능에 이점

## 캐싱 기법

- **Local Cache**
  - 서버 마다 캐시를 따로 저장한다
  - 서버 내에서 작동하기 때문에 속도가 빠르다
  - 다른 서버와 데이터 공유가 어렵다
  - 로컬 서버 장비의 resource를 이용한다. (메모리, 디스크)

- **Global Cache**
  - 여러 서버에서 캐시 서버에 접근하여 사용하므로 분산된 서버에서 데이터를 조회, 저장할 수 있다
  - 네트워크를 통해 데이터를 가져오므로, 상대적으로 느리다
  - 별도의 캐시 서버를 이용하기 때문에 데이터 공유가 쉽다

<br>

참고

[우아한Tech 캐싱](https://www.youtube.com/watch?v=JBFT4KyEvoY)
