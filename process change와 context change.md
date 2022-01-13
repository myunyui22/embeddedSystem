## context change
* cpu에서 실행중인 프로세스가 변경되면 cpu의 레지스터 값도 변경되야 한다
* 레지스터 값이 변경되기 전에 값을 저장하여 ready 혹은 block 된 프로세스가 다시 실행될 때 이어서 실행하도록 하는 작업을 context change라 한다
* context change는 시스템에 많은 부담을 준다
* 캐쉬는 cpu와 메인메모리 사이에 위치하고 있으며 이전 상태의 메모리 정보를 저장해두었다가 cpu에서 요청 시 메인메모리를 거치지 않고 전달한다
* process context change는 기존 캐쉬 정보를 모두 지우고 새로 저장하는 반면 thread context change는 공유하는 데이터가 있으므로 캐쉬를 모두 지우지 않는다. 따라서 context change에 걸리는 시간도 줄어든다

## process change
* context change 중에서 프로세스간 change가 일어나는것을 의미하는듯하다(...)
* 위에서 설명했듯이 프로세스간에는 자원 공유가 안되기 때문에 process change가 일어날 경우 시간이 많이 걸리고 캐시 사용 효율도 좋지 않다


--------------------------------------------------------------
## process와 thread의  상속
* 프로세스는 자식 프로세스가 부모 프로세의 핸들테이블을 상속받으나 모든 영역(code, data, heap, stack)이 독립적으로 이루어지므로 자원을 공유하지 않는다
* 따라서 프로세스간 데이터를 공유하기 위해선 [IPC](http://)(inter Process Communication)이 필요하다
* 쓰레드는 각자 고유의 threadStack을 제외한 나머지를 부모 프로세스와 공유한다
