## Race Condition

> #### 두 개 이상의 프로세스 또는 스레드들이 하나의 공유자원에 동시에 접근을 시도 할 때, 접근 순서에 따라 결과값이 달라질 수 있는 상태.

----

#### Race Condition이 발생하는 경우

1. ##### 커널 작업을 수행하는 중에 인터럽트 발생

   - 문제점 : 커널모드에서 데이터를 로드하여 작업을 수행하다가 인터럽트가 발생하여 같은 데이터를 조작하는 경우
   - 해결법 : 커널모드에서 작업을 수행하는 동안, 인터럽트를 disable 시켜 CPU 제어권을 가져가지 못하도록 한다.

2. ##### 프로세스가 'System Call'을 하여 커널 모드로 진입하여 작업을 수행하는 도중 문맥 교환이 발생할 때

   - 문제점 : 프로세스1이 커널모드에서 데이터를 조작하는 도중, 시간이 초과되어 CPU 제어권이 프로세스2로 넘어가 같은 데이터를 조작하는 경우 ( 프로세스2가 작업에 반영되지 않음 )
   - 해결법 : 프로세스가 커널모드에서 작업을 하는 경우 시간이 초과되어도 CPU 제어권이 다른 프로세스에게 넘어가지 않도록 함

3. ##### 멀티 프로세서 환경에서 공유 메모리 내의 커널 데이터에 접근할 때

   - 문제점 : 멀티 프로세서 환경에서 2개의 CPU가 동시에 커널 내부의 공유 데이터에 접근하여 조작하는 경우
   - 해결법 : 커널 내부에 있는 각 공유 데이터에 접근할 때마다, 그 데이터에 대한 lock/unlock을 하는 방법

</br>

### 동기화
프로세스 또는 스레드가 하나의 공유자원에 접근하는 순서를 정하여 Race Condition을 제거하고 공유자원의 결과 값의 일관성을 보장하는 것이다.

### 임계 영역 
각 프로세스 또는 스레드가 공유자원의 값을 변경하는 코드 영역으로 둘 이상의 프로세스 또는 스레드가 동시에 접근하면 안되는 영역이다. </br>
=> 한 순간에 하나의 프로세스 또는 스레드만이 임계영역(Critical Section)에 접근하여 공유자원의 값을 변경하도록 한다.




(출처) [tech-interview-for-developer](https://github.com/gyoogle/tech-interview-for-developer) , https://parksb.github.io/article/10.html

