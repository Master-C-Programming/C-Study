0910 Study
------

# 메모리 구조와 변수

### 하드웨어 관점에서의 메모리 공간

* 메모리의 종류 : hard disk, RAM, register, cache....

* 하드의 단점 보완을 위해 RAM 추가

* 속도 : 레지스터 > 캐쉬 > 램 > 하드디스크
  
* 가상메모리(virtual memory) : 운영체제가 통으로 구성해주는 메모리 

* 가상메모리의 구분
  - 코드 영역 : 실행할 프로그램의 코드를 저장할 공간
  - 데이터 영역 : 프로그램이 종료될 때까지 유지해야 할 데이터 저장
  - 스택 영역 : 아주 잠깐 사용하고 삭제할 데이터의 저장공간
  - 힙 영역 : 프로그래머가 원하는 방식으로 쓸 수있는 공간

### 변수의 종류에 따른 특성과 할당 위치

* 지역변수 VS 매개변수 : 초기화 방식이 다름