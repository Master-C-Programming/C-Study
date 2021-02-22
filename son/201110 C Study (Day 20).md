20-11-10 C Study (Day 20)
=====
교제 : 윤성우의 열혈 C 프로그래밍

chapter 22 : 구조체와 사용자 정의 자료형1  

<hr>

## 구조체란?

하나 이상의 변수를 묶어서 새로운 자료형을 정의하는 도구  

예를들어 x좌표와 y좌표를 받는다고 하면 이 둘을 묶어서 관리하는 것이 데이터 관리에 더 편리할 것이다.  

### 구조체 변수의 선언과 접근

```c
struct point
{
	int xpos;
	int ypos;
};

struct person
{
	char name[20];
	char phoneNum[20];
	int age;
}
```
위와같이 `point`는 `int xpos`와 `int ypos`를 묶은 새로운 구조체 자료형이 되는 것이고  
`person`은 `char`형의 배열 2가지와 `int age`를 갖는 새로운 구조체 자료형이다.

위의 내용은 구조체 자료형을 선언한 것이고 구조체 변수를 만드는 방법은 다음과 같다.

`struct point decPos;`  
`struct person man;`  
이렇게 되면 메모리 공간에는 `point`형 구조체 변수 `decPos`와 `person`형 구조체 변수 `man`이 선언되는 것이다.

이제 decPos의 맴버로의 접근과 man을 초기화 해보자  

```c
// 맴버 변수로의 접근
pos.xpos = 10;	// 접근할 요소에 . 을 찍고 접근하면 된다.
pos.ypos = 20;

// int num = 7; 과 비슷한 선언과 동시에 초기화
struct person man = {"손동완", "010-1234-7777", 23};
```

### 구조체 배열과 포언터

구조체라고 해서 전혀 다를 게 없다.  

```c
// 각각의 첫 번째, 두 번째, 세 번째 요소의 초기화
struct person arr[3] = {
	{"홍길동", "010-1212-4862", 23},
	{"김기철", "010-1818-1590", 18},
	{"고길동", "010-2222-5252", 30}
};
```

구조체로 정의한 자료형의 포인터 선언을 할 수 있는데 이는 다양한 자료구조에 활용된다.

```c
// point 내부에 point형 포인터를 선언
struct point
{
	int xpos;
	int ypos;
	struct point * ptr;
} pos1, pos2, pos3;

pos1.ptr = &pos2;
pos2.ptr = &pos3;
pos3.ptr = &pos1;
```
위와 같이 pos1, pos2, pos3을 연결할 수 있다.  

#### 구조체의 주소 값과 크기

구조체 변수의 주소 값은 첫 번째 멤버의 주소 값과 같다.
마치 배열 이름의 주소 값이 배열의 첫 번째 요소의 주소 값과 같은 원리이다.  
구조체의 크기는 `sizeof()`연산자로 알아본 결과 그냥 배열과 같이 각각의 요소의 크기를 합한 값과 같다.  
