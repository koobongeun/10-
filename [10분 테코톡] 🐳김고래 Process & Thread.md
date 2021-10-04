# [10분 테코톡] 🐳김고래 Process & Thread

## Process

process : 실행중인 Program 운영체제로부터 시스템 자원을 할당 받는 작업의 단위

<br>

process 구성

- Stack : 매개변수, 지역 변수 등 임시적인 자료
- Heap : 동적으로 할당되는 메모리
- Data : 전역 변수
- Text : Program의 코드

<br>

Operating System

- 여러 Process의 집합

<br>

PCB(Process Control Block)

- 각 프로세스는 운영체제에서 PCB로 표현
- PID : 프로세스 식별자
- 프로세스 상태 : new, ready, running, waitng, halted 등
- 프로그램 카운터 : 다음 실행할 명령어의 주소
- 스케줄링 정보 : 우선 순위 등

<br>

## Thread

thread

- 프로세스 내에서 실행되는 흐름의 단위
- cpu 이용의 기본 단위
- Text, Data, Heap 영역을 공유
- 각 Thread 별도의 Stack 영역을 가짐

<br>

## Multi Thread

multi thread

- 프로세스의 자원을 공유
- 향상된 응답성
- Context Switching 비용이 적음
- 자원을 공유하는 만큼, 충돌을 주의'
- ex) web server(html, css js 이미지, 아이콘 등등을 멀티 스레드로 할당 받는다.)

<br>

## Multi Process

- 하나의 작업을 여러 개의 프로세스가 처리
- 프로세스간 통신(IPC, Interprocess communication), 파이프 나 다른걸로 연결 해야함
- Context Switching 비용이 큼
- 자식 프로세스 중 하나가 문제가 생겨도 다른 프로세스에 영향이 없음
- ex) Google Chrome (탭마다 킬 수 있는거) >> Browser Process, Render Process, GPU Process, Plugin Process
