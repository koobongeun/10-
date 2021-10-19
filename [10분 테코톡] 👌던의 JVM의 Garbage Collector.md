# [10분 테코톡] 👌던의 JVM의 Garbage Collector

## JVM (Java Virtual Machine)

운영체제의 메모리 입력에 접근하여 메모리를 관리하는 프로그램

- 메모리 관리
-   Grabage Collector 수행

<br>

##  Garbage Collector

동적으로 할당한 메모리 영역 중 사용하지 않는 영역을 탐지하여 해제하는 기능

## Stack, Heap

Stack 

- 정적으로 할당한 메모리 영역
- 원시 타입의 데이터가 값과 함께 할당,  Heap영역에 생성된 Object 타입의 데이터의 참조 값 할당

Heap

- 동적으로 할당한 메모리 영역
- 모든 Object 타입의 데이터가 할당, Heap영역의 Object를 가리키는 참조 변수가 Stack에 할당

## Garbage Collector(Mark and Sweep)  과정

1. Garbage collector가 Stack의 모든 변수를 스캔하면서 각각 어떤 객체를 참조하고 있는지 찾아서 마킹한다.
2. Reachable Object가 참조하고 있는 객체도 찾아서 마킹한다.
3. 마킹되지 않은 객체를 Heap에서 제거한다.
4. 1~2은 Mark 과정 3은 Sweep과정

<br>

## Garbage Collector 종류

1. Serial GC 
   - GC를 처리하는 스레드 1개이다. 
   - CPU코어가 1개만 있을 떄 사용하는 방식
   - Mark-Compact collection 알고리즘 사용
   
2. Paralle GC
   -  GC를 처리하는 스레드가 여러 개 이다.
   - Serial GC보다 빠르게 객체를 처리할 수 있다.
   - Parallel GC는 메모리가 충분하고 코어의 개수가 많을 떄 사용하면 좋다.

3. Concurrent Mark Sweep GC

   (1) Stop-The-World

   - GC을 실행하기 위해 JVM이 애플리케이션 실행을 멈추는 것이다.
   - stop-the-world가 발생하면 GC를 실행하는 스레드를 제외한 나머지 스레드는 모두 작업을 멈춘다.
   - GC 작업을 완료한 이후에 중단한 작업을 다시 시작한다.

   (2) 개념

   - stop-the-world 시간이 짧다.
   - 애플리케이션의 응답 시간이 빨라야 할 때 CMS GC를 사용한다.
   - 다른 GC 방식보다 메모리와 CPU를 더많이 사용한다.
   - Compaction 단계가 제공되지 않는다.

4. G1 GC
   - 각 영역을 Region 영역으로 나눈다.
   - GC가 일어날 떄, 전체영역(Eden, Survival, Old generation)을 탐색하지 않는다.

