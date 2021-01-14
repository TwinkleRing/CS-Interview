## 프로세스 상태(Process State)

OS가 하는 역할 중 프로세스 관리는 가장 중요한 역할이라고 할 수 있다.
프로세스는 실행중인 프로그램이고 상태(State)를 가지고 있다.


#### 프로세스 상태 전이도

![image](https://user-images.githubusercontent.com/43642411/104544350-de3d1800-566a-11eb-8704-aaf4e4c56b0a.png)


#### 상태
- New : 프로그램이 실행되어 메인 메모리에 할당된 상태. </br>
- Ready : 메인 메모리에 할당된 프로그램이 초기화 작업을 통해 실행 준비를 모두 마치고 CPU가 할당되기를 기다리는 상태. </br>
- Running : CPU가 할당되어 프로세스가 작업을 수행중인 상태. </br>
- Waiting : I/O 이벤트가 발생하여 실행중인 프로세스가 중단되고 I/O 처리가 완료될 때까지 대기하는 상태  </br>
- Terminated : 프로세스가 실행을 완료하여 종료될 때의 상태 </br> </br>
- Suspended Waiting : 프로세스가 대기 상태에서 주 기억 장치를 잃은 상태.
- Suspended Ready : 프로세스가 기억장치를 제외한 다른 모든 필요한 자원들을 보유한 상태. </br>

--- 

![image](http://itwiki.kr/images/e/e9/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EC%83%81%ED%83%9C%EC%A0%84%EC%9D%B4%EB%8F%84_%EC%83%81%EC%84%B8.png)

#### 상태 전이
- Time Run out : 해당 프로세스가 작업을 완료하기전에 할당된 CPU 시간을 모두 소모하여 인터럽트에 의해 강제로 Ready로 변하고 <br>CPU는 다른 프로세스를 실행시킨다.</br>
- Dispatch : Ready 상태의 프로세스 중에 하나를 우선순위에 따라 CPU를 할당하여 Running 상태로 전이된다. </br>
- Wake up : I/O 작업이 완료되어 Waiting 상태에서 Ready 상태로 전이되는 과정
- Block : 프로세스가 실행되는 중 I/O(입출력)이나 자원 등을 기다리기 위해 대기로 전환. </br></br>
- Swap - out : 준비 상태에서 주 기억 장치를 반납하고 지연 준비(지연 대기) 상태로 전이.
- Swap - in : 지연 준비(지연 대기) 상태에서 주 기억 장치에 적재되어 준비상태로 전이.


#### PCB
