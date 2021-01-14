### PCB(Process Control Block)란?
  - 운영체제가 프로세스를 제어하기 위해 정보를 저장해 놓은 곳으로, 프로세스의 상태 정보를 저장하는 저장 장소
  - 프로세스 상태 관리와 문맥 교환(Context Switching)을 위해 필요하다.
  - PCB는 프로세스 생성 시 같이 만들어지며 주기억장치에 유지되고 프로세스가 종료되면 제거된다. </br>

#### Process Management
> CPU가 프로세스가 여러 개 일때 이들을 CPU 스케줄링을 통해 관리하는 것. 
CPU는 각 프로세스들이 누구인지 알아야 관리가 가능합니다. </br>각 프로세스의 특징을 갖고있는 것이 **Process Metadata**

**Process Metadata**
   - Process ID
   - Process State
   - Process Priority
   - CPU Registers
   - Owner
   - CPU usage
   - Memory Usage
   
이 메타데이터는 프로세스가 생성되면 PCB에 저장된다.


#### PCB가 필요한 이유
프로세스는 작업을 처리하다가도 상태가 전이되면 작업 내용들을 모두 정리하고 CPU를 반납해야한다. </br>
이때 진행하던 작업들을 모두 저장하지 않으면 다음에 자신에게 다시 CPU가 할당되어도 어떠한 작업을 해야하는지 알 수 없는 사태가 발생.</br>
따라서 프로세스는 처리하던 작업의 내용들을 자신의 PCB에 저장하고, </br> 다음에 다시 작업을 수행할 때 PCB로부터 해당 정보들을 CPU로 가져와서 계속해서 하던 작업을 진행합니다.


![image](https://3.bp.blogspot.com/-GWru8c5JVF8/WvNAuURo5wI/AAAAAAAAATg/7eZ8FGgQTqke7jTCDRQX4eY22nCQsQv1QCLcBGAs/s1600/PCB.PNG)
