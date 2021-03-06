# 💡 **프로세스 vs 쓰레드**

- **프로세스**
  - 운영체제로부터 자원을 할당받은 **작업 단위**
  - 메모리에 올라와 실행되고 있는 프로그램의 인스턴스(독립적인 개체)
  - 프로세스는 1개 이상의 쓰레드를 가지고 있다.

- **쓰레드**
  - 프로세스 내에서 **실행되는 흐름**의 단위
  - 쓰레드는 프로세스 내에서 각각 Stack만 따로 할당받고 Code, Data, Heap 영역은 공유한다.

<br>

프로그램 → 프로세스 → 쓰레드

프로그램이란, 어떤 작업을 위한 정적인 상태의 파일을 말한다. 프로그램을 실행함으로써 해당 파일은 메모리를 할당받게되고, 이 상태를 동적인 상태라고 하며 프로세스가 된다.

프로세스가 할당받는 시스템 자원
- 주소공간
- Code, Data, Stack, Heap의 구조의 독립된 메모리 영역

쓰레드는 프로세스의 자원을 이용하여 작업을 수행한다.

<br>

- **멀티 프로세스와 멀티 쓰레드**

  멀티 프로세스는 여러개의 프로세스를 생성하여 하나의 작업을 병렬적으로 처리하는 과정을 의미하고 멀티 쓰레드는 하나의 프로세스 내에서 여러개의 쓰레드를 생성함으로써 작업을 처리하는 과정을 의미한다. 이 둘의 공통점은 여러 작업을 동시에 혹은 병렬적으로 처리함으로써 작업 속도를 높일 수 있다는 장점이 있다.
  
  - 멀티 프로세스에서 발생할 수 있는 문제점
  
      CPU는 한 번에 한개의 프로세스만 처리가 가능하다. 여러 작업이 동시에 실행되는 것처럼 보이지만 CPU는 계속해서 프로세스들을 바꿔주는 일을 내부적으로 진행하고 있다. 이렇게 하나의 프로세스에 대한 정보들을 저장해놓고, 새로운 프로세스에 대한 정보를 가져오고 메모리를 할당해주는 과정을 **문맥 교환**이라고 한다. 이 문맥교환이 이뤄지기 위해 운영체제에서는 **시스템 콜**이라는 절차를 진행하게 된다. 문맥 교환동안에 CPU는 아무 작업을 하지 못하므로 오버헤드 발생의 가능성이 있으며 CPU성능 저하가 될 수 있다.
  
  - 멀티 쓰레드의 장점
  
      쓰레드는 메모리 공간을 멀티 프로세스에 비해 적게 차지한다는 장점이 있다. 쓰레드의 **문맥교환**은 프로세스의 문맥교환과 달리 Cache Memory를 비울 필요가 없기 때문에 속도면에서 훨씬 더 빠르고 CPU의 부담도 훨씬 덜 가게 된다. 이러한 점 때문에 시스템의 처리율이 향상되고 프로그램의 응답시간이 단축되어 진다.
  
- **무조건 멀티 쓰레드를 사용하는 것이 좋을까?**

  쓰레드는 프로세스와 달리 서로 독립적이지 못하므로 오류가 생길 시에 같은 메모리 영역을 공유하고 있는 다른 쓰레드에게도 영향을 미칠 수 있다. 역으로 멀티 프로세스는 서로 독립적으로 존재하기 때문에 오류에 영향을 받지 않고 정상적으로 실행이 가능하다.

- **문맥교환**

   새로운 프로세스에 대한 정보를 가져오고 메모리를 할당해주는 과정을 문맥 교환이라 하는데 프로세스의 문맥교환과 달리 쓰레드의 문맥 교환은 캐시 메모리를 비울 필요가 없어져서 속도가 빠르다.

