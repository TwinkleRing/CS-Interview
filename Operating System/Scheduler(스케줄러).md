## 프로세스 스케줄러(Scheduler)
> **한정적인 메모리를 여러 프로세스가 효율적으로 사용할 수 있도록 다음 실행 시간에 실행할 수 있는 프로세스 중에 하나를 선택하는 역할**
프로세스가 생성되어 완료될때까지 프로세스는 여러 종류의 스케줄링 과정을 거치게 됩니다.
---

### 프로세스를 스케줄링 하기 위한 Queue
다중 프로그래밍 환경에서는 여러 개의 프로세스를 사용하기 때문에 이런 프로세스들을 관리하기 위해 Queue를 사용합니다.
(다중 프로그래밍이란 CPU 작업과 입출력 작업을 병행하는 것)

* **Job Queue(작업 큐)** <br>
시스템의 모든 프로세스들을 관리하기 위한 Queue 입니다. 프로세스의 상태와 무관하게 현재 시스템 안의 모든 프로세스를 관리합니다.<br>
작업 큐에 있다고해서 반드시 프로세스가 메모리를 할당받은 것은 아닙니다.

* **Ready Queue(준비 큐)** <br>
CPU 할당을 기다리고 있는 프로세스들을 관리하는 Queue입니다. 준비 큐에 있는 프로세스들은 준비 상태에 있게 됩니다. <br>
여기서 프로세스들을 줄 세우는 방법으로 스케줄링 알고리즘(어떻게 공평하게 CPU를 나눠줄까?)를 사용합니다.

* **Device Queue(장치 큐)** <br>
각각의 장치마다 입출력 서비스를 기다리며 대기하는 프로세스들을 관리하는 Queue 입니다. <br>
장치 큐에 속한 프로세스는 봉쇄 상태(blocked)가 되고 해당 장치의 서비스를 받으면 장치 컨트롤러가 인터럽트를 발생시켜<br> 준비 상태로 바뀌어 준비 큐로 이동합니다.

### 프로세스 스케줄러의 종류
스케줄링은 시스템의 목표를 달성할 수 있도록 프로세서(CPU)를 할당하는 일련의 과정.
각각의 Queue 에 프로세스들을 넣고 빼주는 스케줄러에도 3가지 종류가 있습니다.

#### 1. 장기 스케줄러(Long term scheduler & Job scheduler) 

어떤 프로세스를 준비 큐에 넣을 것인가? <br>

* 메모리와 디스크 사이의 스케줄링 담당
* 프로세스에 메모리 및 각종 리소스 할당
* Degree of Multiprogramming 제어(실행중인 프로세스의 수 제어)
* 프로세스의 상태는 New -> Ready


**장기 스케줄러(작업 스케줄러)** 는 어떤 프로세스를 준비 큐에 넣을 지를 결정하는 역할을 합니다.<br>
디스크와 메모리 사이에서 스케줄링을 담당하여 어떤 프로그램을 가져와 메모리를 할당하여 프로세스로 만들고 준비 큐에 넣을지 결정합니다.<br>
장기 스케줄러는 수십 초 내지 수분 단위로 가끔 호출되기 때문에 상대적으로 속도가 느린 것이 허용됩니다.<br>
또한 메모리에 동시에 올라가 있는 프로세스의 수를 조절하는 역할을 합니다.<br>
현대의 **시분할 시스템**에서 사용되는 운영 체제에는 일반적으로 장기 스케줄러를 두지 않는 경우가 대부분입니다.<br>
과거에는 적은 양의 메로리를 많은 프로세스들에게 할당하면 프로세스당 메모리 보유량이 적어져 장기 스케줄러가 조절하는 역할을 했지만<br>
현대의 운영체제에서는 프로세스가 시작되면 바로 그 프로세스에 메모리를 할당해 Ready 상태가 됩니다.<br>
   
---

#### 2. 단기 스케줄러(Short term scheduler & CPU scheduler)

어떤 프로세스에게 **CPU(프로세서)** 를 할당해 줄 것이가? <br>

* CPU와 메모리 사이의 스케줄링을 담당.
* Ready Queue에 존재하는 프로세스 중 어떤 프로세스를 Running 시킬지 결정하는 역할.
* 프로세스에 CPU를 할당(Dispatch)
* 프로세스의 상태는 Ready -> Running -> Waiting -> Ready


**단기 스케줄러** 는 준비 큐에 있는 프로세스 중에서 어떤 프로세스를 다음 번에 실행 상태로 만들 것인지를 결정합니다. <br>
시분할 시스템에서 타이머 인터럽트가 발생하면 단기 스케줄러가 호출됩니다.<br>
단기 스케줄러는 호출되면 미리 정해진 스케줄링 알고리즘에 따라 CPU를 할당할 프로세스를 선택합니다.<br>

---

#### 3. 중기 스케줄러(Medium term scheduler & Swapper)

메모리에 적재된 프로세스의 수를 동적으로 관리, 조절하기 위한 스케줄러.<br>

* 메모리 여유 공간 확보를 위해 프로세스를 통째로 메모리에서 디스크로 쫓아냄(Swapping)<br>
* 프로세스에게서 메모리를 Deallocate<br>
* Degree of Multiprogramming 제어(실행중인 프로세스의 수 제어)<br>
* 프로세스의 상태는 Ready -> Suspended<br>
* 현재 시스템에서 메모리에 너무 많은 프로그램이 동시에 올라가는 것을 조절하는 스케줄러.<br>


시스템에서 메모리에 많은 수의 프로세스가 적재되면 프로세스 당 보유하고 있는 메모리량이 매우 적어지게 됩니다.<br>
중기 스케줄러는 이를 완화시키기 위해 일부 프로세스를 메모리에서 디스크로 스왑 아웃(swap out)시키는 역할을 수행합니다.<br>
(swap out이란 메모리를 빼앗아 그 내용을 디스크에 스왑 영역에 저장해두는 것)<br>

중기 스케줄러가 프로세스들을 스왑 아웃시키면 프로세스는 중지 상태가 됩니다.<br>
중지 상태Suspendend)는 외부적인 이유로 프로세스의 수행이 정지된 상태로 메모리에서 내려지고 디스크로 쫓아내진 것을 의미합니다.<br>
이 중지 상태는 다른 I/O 작업을 기다리는 blocked 상태와 달리 스스로 Ready 상태로 돌아갈 수 없습니다. <br>

----

 
참조) https://kosaf04pyh.tistory.com/190 , https://parksb.github.io/article/9.html
