## Database Lock

데이터베이스의 Lock은 트랜잭션들이 **동시에** 수행될 때, 데이터의 **일관성**을 해치지 않도록 데이터 접근을 제어한다.

## Lock의 종류

동시성 제어는 어떻게 할까?

- **낙관적 Lock**
    - 트랜잭션 대부분은 충돌이 발생하지 않는다고 가정
    - 동시 업데이트가 거의 없는 경우 
    
- **비관적 Lock**
    - 트랜잭션 충돌이 발생한다고 가정
    - 하나의 트랜잭션이 자원에 접근 시 Lock을 걸고, 다른 트랜잭션이 접근하지 못하게 한다.
    - 동시 업데이트가 빈번한 경우
    - 공유 Lock과  베타 Lock이 있다.

### 공유 락(Shared Lock)과 베타 락(Exclusive Lock)

- **공유 Lock**은 데이터를 읽을 때 사용되는 Lock으로, 공유 Lock끼리는 동시 접근이 가능하다. 즉, 데이터를 다른 사용자가 동시에 read할 수 있지만 write는 불가능하다. 만약 특정 데이터에 공유 Lock이 걸려있다면, 베타 Lock을 사용할 수 없고 여러 공유 Lock은 동시에 적용될 수 있다.

- **베타 Lock**은 데이터를 변경하고자 할 때 사용되며, 해당 트랜잭션이 완료될 때까지 다른 트랜잭션에서 read나 write할 수 없다. 베타 Lock 연산을 실행한 트랜잭션만 해당 데이터에 대한 독점권을 가지므로 다른 트랜잭션이 베타 Lock을 걸 수 없다.

## Lock으로 발생할 수 있는 문제점

### 블로킹(Blocking)

블로킹이란 Lock들의 경합이 발생하여 특정 트랜잭션이 작업을 진행하지 못하고 멈춰 선 상태로, 데이터에 대해 하나의 트랜잭션이 **베타 Lock**을 걸면 다른 트랜잭션들은 Lock을 걸지 못하고 **대기**해야하기 때문에 발생한다. 블로킹을 해소하기 위해서는 이전 트랜잭션이 commit 혹은 rollback 되어야 한다.

- 블로킹 해결방안
    - 트랜잭션을 짧게 정의
    - 같은 데이터를 갱신하는 트랜잭션은 동시에 수행되지 않도록 설계
    - LOCK TIMEOUT을 이용하여 잠금해제 시간을 조절

### 데드락(Deadlock)

![img](https://github.com/dilmah0203/TIL/blob/main/Image/Deadlock.png)

트랜잭션1이 리소스1에 대해 베타 Lock을 걸고, 트랜잭션2가 리소스2에 공유 Lock을 걸었다고 가정하자. 트랜잭션2가 리소스1에게 공유 Lock을 걸어야 하는데 이미 베타 Lock이 걸려있어 대기하게된다. 또한 트랜잭션1도 트랜잭션2가 리소스2에 걸어놓은 공유 Lock 때문에 대기할 수 밖에 없다. 트랜잭션이 서로가 서로를 기다리게 되어 무한 대기 상태에 빠지는 것이 Deadlock이다.

- 데드락 해결방안
    - 트랜잭션 진행방향을 같은방향으로 처리하게되면 블로킹 문제가 발생하지만, 데드락 발생 확률이 줄어든다.
    - 트랜잭션 처리속도를 최소화
    - LOCK TIMEOUT을 이용하여 잠금해제 시간을 조절
