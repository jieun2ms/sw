# 리눅스 명령어(top, ps, jobs, kill)

**top**

top 명령어는 현재 OS의 상태를 나타내주는 CLI 어플리케이션이다.
메모리 사용량, CPU 사용량 등을 나타내주며 top를 실행하는 동안에는 주기적인 업데이트를 하여 실시간으로 현재 OS의 상태를 출력해줌으로써 OS문제가 있을시 원인을 찾을수 있는 명령어 중 하나이다.

옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여준다.

**top 실행 전 옵션**

순간의 정보를 확인하려면 -b 옵션 추가(batch 모드)

-n : top 실행 주기 설정(반복 횟수)

**top 실행 후 명령어**

shift + p : CPU 사용률 내림차순

shit + m : 메모리 사용률 내림차순

shift + t : 프로세스가 돌아가고 있는 시간 순

k : kill. k 입력 후 PID 번호 작성. signal은 9

f : sort field 선택 화면 -> q 누르면 RES순으로 정렬

a : 메모리 사용량에 따라 정렬

b : Batch 모드로 작동

1 : CPU Core별로 사용량 보여줌




**jobs**

백그라운드로 실행 중인 프로세스나 현재 중지된 프로세스의 목록을 출력해 주는 명령이다.
jobs 명령어의 기본 형식
jobs [OPTIONS] [JOB]
jobs 명령어는 옵션이나 인자 없이 주로 사용한다. 단, 실행중인 작업이 없다면 아무것도 출력되지 않는다.

**jobs 명령어에서 사용할 수 있는 주요한 옵션**

-l 옵션: 프로세스 ID와 함께 잡 목록을 출력, 프로세스에 번호를 추가하여 출력

-n 옵션: 상태 변화를 일으킨 작업만 출

-p 옵션: 잡의 프로세스 ID만 출력

-r 옵션: 실행 중인 잡만 출력

-s 옵션: 중지된 잡만 출력


**kill**

kill 명령어는 프로세스에 시그널(signal)을 보내어 원하는 동작을 수행할 수 있다. 
프로세스 종료 외에도 다른 신호를 보내어 프로세스의 동작을 제어할 수도 있다.
kill 명령어를 사용하기 위해서는 먼저 종료하려는 프로세스의 프로세스 ID(PID)를 알아야 한다. 
일반적으로 ps 명령어를 사용하여 현재 실행 중인 프로세스 목록을 확인한 후, 종료하려는 프로세스의 PID를 찾아야 한다. 그런 다음 kill 명령어를 사용하여 해당 PID의 프로세스를 종료할 수 있다.

**kill 명령어의 구문**

kill [옵션] <PID>

여기서 <PID>는 종료할 프로세스의 식별자인 프로세스 ID를 나타낸다.


**kill 명령어 다양한 옵션**

-s <signal>: 특정 시그널(signal)을 사용하여 프로세스를 종료한다. 기본적으로 SIGTERM 시그널이 사용된다.

-l, --list: 지원되는 시그널(signal) 목록을 출력

-a, --all: 현재 사용자에 속한 모든 프로세스를 종료한다.

-q, --queue: 프로세스에 시그널을 보내는 대신 시그널을 대기열에 추가한다.

kill 명령어의 자세한 설명과 사용 가능한 옵션은 man kill 명령어를 통해 확인할 수 있다.


**kill 명령어를 사용하여 프로세스를 종료하는 예시**

현재 실행 중인 프로세스의 목록을 확인한다: bash ps -ef

종료하려는 프로세스의 PID를 확인한다.

**kill 명령어의 장점과 단점**

장점: - 간단한 명령어로 빠르게 프로세스를 종료할 수 있다. - 다양한 옵션을 사용하여 프로세스 동작을 제어할 수 있다.

단점: - 잘못 사용하면 의도치 않은 프로세스 종료가 발생할 수 있다. - SIGKILL 시그널을 사용하여 강제 종료할 경우, 프로세스가 올바르게 정리되지 않을 수 있고, 데이터 손실 등의 문제가 발생할 수 있다.

**ps**

ps 명령어는 현재 실행 중인 모든 프로세스의 정보를 보여주는 유용한 도구이다.

**ps 명령어 사용법**

ps [options]

**ps 명령어의 여러 옵션**

-e: 시스템 내의 모든 프로세스들을 보여준다. 시스템상의 모든 프로세스에 대한 정보 출력

-f: 프로세스별로 상세한 정보를 보여준다.

-u: 사용자별로 프로세스를 보여준다.  사용자의 프로세스 출력

-l: 긴 형식으로 프로세스 정보를 출력합니다.

옵션을 조합하여 원하는 정보를 얻을 수 있다. 예를 들어, ps -ef 명령어는 모든 프로세스의 상세 정보를 보여준다.

**ps 명령어의 장단점**

장점

ps 명령어를 사용하면 현재 실행 중인 모든 프로세스의 정보를 한 눈에 확인할 수 있다.

다양한 옵션을 사용하여 원하는 조건에 따른 프로세스만 필터링할 수 있다.

단점

ps 명령어는 현재 상태의 스냅샷을 보여주기 때문에 실시간으로 변하는 프로세스 상태를 확인하기에는 적합하지 않을 수 있다.

모든 프로세스를 보여준다는 점에서 출력 결과가 많을 수 있기 때문에 원하는 정보를 찾기에 다소 어려움이 있을 수 있다.

ps 명령어는 기본적으로 현재 실행 중인 프로세스를 보여주지만, -C 옵션을 사용하면 특정 프로세스만 필터링할 수 있다. 예를 들어, ps -C nginx는 nginx라는 이름을 가진 프로세스만 보여준다.

또한, ps 명령어와 함께 grep 명령어를 사용하면 원하는 조건에 맞는 프로세스만 필터링할 수 있다. 
예를 들어, ps -ef | grep nginx는 nginx 프로세스로 필터링된 결과만 보여준다. 이를 통해 보다 세밀한 프로세스 관리가 가능해진다.
