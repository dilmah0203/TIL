## Deadlock

Deadlock은 **교착 상태**를 의미하는데, 교착 상태란 **프로세스가 자원을 얻지 못해 다음 처리를 진행하지 못하는 상태**를 말한다. 교착 상태가 발생할 수 있는 영역을 임계 영역이라고 한다.

### Deadlock 발생 조건

네 가지 조건을 모두 만족하면 Deadlock이 발생한다. 따라서 아래의 4가지 조건 중 하나라도 만족되지 못하면 Deadlock이 발생하지 않는다.

1. **상호 배제(Mutual exclusion)** : 하나의 공유 자원에 대해 두 개 이상의 프로세스가 동시에 접근할 수 없다.

2. **점유와 대기(Hold and wait)** : 하나의 자원을 점유하고 있는 프로세스가 있고, 해당 프로세스가 다른 프로세스에서 자원을 얻기 위해서는 요청을 하고 대기해야 한다.

3. **비선점(No preemption)** : 특정 프로세스가 어떤 자원을 사용하고 있을 때 그 해당 자원 사용이 끝나기 전까지는 그 자원을 뺏을 수 없다.

4. **순환 대기(Circular wait)** : 프로세스들이 서로 사용하고 있는 자원에 대해서 순환적으로 대기한다.

### Deadlock 해결 방법

- **교착 상태 예방** : 교착 상태가 발생되지 않도록 사전에 예방하는 것으로, Deadlock 발생 조건 중 하나를 제거함으로써 해결하는 방법이다. 일반적으로 자원 사용 효율성이 떨어지고 비용이 많이 드는 방법이다.
  - 상호 배제 부정 : 여러 프로세스가 공유 자원을 사용할 수 있게 함
  - 점유 대기 부정 : 프로세스 실행 전 모든 자원을 할당함
  - 비선점 부정 : 자원 점유 중인 프로세스가 있어도 다른 프로세스가 자원을 요구하면 자원 반납
  - 순환 대기 부정 : 자원에 고유 번호를 할당하여 순서대로 자원을 요구하도록 함

- **교착 상태 회피** : 교착 상태 발생 가능성을 검사해서 발생 가능성이 있다면 사전에 회피하는 방식이다. 자원을 요청할 때마다 시스템 검사를 하는 만큼 오버헤드가 크다. 
  - 자원 할당 그래프 알고리즘 : 프로세스가 자원을 요청하고 자원이 프로세스에게 할당 되는 방향성을 가진 그래프로써, Deadlock 발생 여부를 탐지 할 수 있는 그래프다.
 
![img](https://github.com/dilmah0203/TIL/blob/main/Image/Resource_Allocation%20Graph%20Algorithm.png)

클레임 화살표는 프로세스가 자원을 요청 할 수도 있다는 것을 의미한다. 시스템은 위와 같은 그래프를 유지하며, 프로세스로 부터 자원에 대한 요청을 받으면 순환 대기 상태가 발생하지 않는 경우에만 자원을 할당 한다. 위 예에서 프로세스P2가 자원 R2에 대한 요청을 한다면, 시스템은 현재 R2가 어떠한 프로세스에게 할당 되지 않은 상태라고 할지라도 P2에게 바로 할당해주지 않고, 대기 시킨다. 이유는 P1에서 R2로 그려져 있는 클레임 화살표 때문이다. 이는 언제든지 프로세스 P1이 R2의 자원을 요청 할 수 있다는 것을 의미하고,만일 그 시점이 P2가 R2를 할당 받고 난 후라면, P1이 자원을 추가 요청함으로써 순환 대기 상태가 발생한다. 시스템은 이를 막기 위해 애초에 P2의 요청을 거절해 버림으로써 데드락을 회피한다.

  - 은행원 알고리즘 : 프로세스가 자원 요청 시, 자원을 할당하게 된다면 안정 상태로 남아 있는지 사전 검사 후 안정 상태라면 자원을 할당하고, 불안정 상태라면 다른 프로세스가 자원을 해지할 때 까지 대기한다.
 
> 안정 상태란?

시스템의 프로세스들이 요청하는 모든 자원을 Deadlock을 발생시키지 않으면서 모두에게 할당해 줄 수 있는 상태. 반대로 불안정 상태는 Deadlock 발생 가능성이 있는 상태를 의미한다.

- **교착 상태 탐지 및 회복** : 교착 상태를 허용하지만 상태를 탐지하고 회복하는 방식이다. 알고리즘을 주기적으로 실행함으로써 시스템에 발생한 Deadlock을 체크하고 회복한다. 교착상태로부터 회복이란 교착상태를 일으킨 프로세스를 종료하거나, 할당된 자원을 해제함으로써 회복하는 거을 의미한다.
  - 프로세스 종료 방식 : 교착 상태의 프로세스를 모두 중지하거나 교착 상태가 제거될 때까지 한 프로세스씩 중지한다.
  - 자원 선점 방식 : 교착 상태가 깨질 때까지 프로세스가 점유한 자원을 선점해 다른 프로세스에게 할당한다. 자원 선점 방식의 고려 사항에는 세 가지가 있다.
    - 희생자 선택 : Deadlock에서 회복 할 때 어떤 프로세스를 죽일 것인지 혹은 어떤 프로세스의 자원을 선점하여 다른 프로세스에게 할당할 것인지 선택한다.
    - 후퇴(Rollback) : 희생자를 선택 하였다면 해당 프로세스를 어느 정도 수준으로 롤백을 시킬 것인지 예를 들어 프로세스를 아예 죽였다가 새로 킬 것인지 재시작을 할 것인지, 아니면 교착 상태가 어느 정도 해결이 될 만큼만 롤백을 시킬 것인지 등을 고려한다.
    - 기아 상태(Starvation) : 기아 상태란 특정 프로세스의 우선순위가 낮아서 원하는 자원을 계속 할당 받지 못하는 상태로, 희생자를 선택할 때에는 한정된 시간 동안에만 희생될 것을 보장해야 한다.

- 교착 상태 무시 : 교착 상태 자체를 무시하고 특별한 조치를 취하지 않는 방법이다. 교착 상태의 발생 확률이 낮은 운영체제에서 주로 사용한다. 교착 상태를 주기적으로 탐지함으로써 얻는 성능저하, 오버헤드보다 차라리 무시하는 것이 나을 경우 사용한다.

<br>

참고

[우아한Tech Deadlock](https://www.youtube.com/watch?v=Ry_gB34cvwc)