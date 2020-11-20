20-11-24 C Study (Day 22)
=====
교제 : 윤성우의 열혈 C 프로그래밍

chapter 23 : 구조체와 사용자 정의 자료형2  

<hr>

## 구조체의 유용함에 대한 논의

학생의 이름, 학번, 학교명, 전공, 학년을 입력받고 해당 학생의 정보를 모두 출력하는 프로그램을 작성한다고 하자.
학생의 정보를 출력하는 함수는 구조체를 사용하지 않으면 5가지의 정보를 갖는 변수를 모두 매개변수 선언을 하여 전달받아야 할 것이다.  
그러나 구조체를 사용한다면 5가지의 정보를 모두 묶어 매개변수로 한 번에 전달해준다면 끝이다.

```c
typedef struct student
{
	char name[20];
	char stdnum[20];
	char school[20];
	char major[20];
	int year;
} Student;

void ShowStudentInfo (Student * sptr)
{
	printf("학생 이름: %s \n", sptr->name);
	printf("학생 고유번호: %s \n", sptr->stdnum);
	printf("학교 이름: %s \n", sptr->school);
	printf("선택 전공: %s \n", sptr->major);
	printf("학년: %d \n", sptr->year);
}
```

### 프로그래밍 예제 1

좌 상단의 x, y 좌표가 [0, 0], 우 하단의 x, y 좌표가 [100, 100]인 좌표평면상의 
직사각형 정보를 표현하기 위한 구조체 Rectangle을 정의하되 앞의 point 구조체 기반으로 정의하자

그리고 Rectangle 구조체 변수를 인자로 전달받아 해당 직사각형의 넓이를 계산하여 출력하는 함수와
직사각형을 이루는 네 점의 좌표정보를 출력하는 함수를 각각 정의해보자.
단, Rectangle 변수 내에는 두 점의 정보만 존재해야 한다.

### 코드 1

```c
#include <stdio.h>

typedef struct
{
	int xpos;
	int ypos;
} Point;

typedef struct
{
	Point pos1;
	Point pos4;
} Rectangle;

void computeArea (Rectangle * rec)
{
	int a, b;
	a = (rec->pos4.xpos - rec->pos1.xpos);
	b = (rec->pos4.ypos - rec->pos1.ypos);
	printf("직사각형의 넓이: %d \n", a*b);
}

void printPoints(Rectangle* rec)
{
	printf("pos1: [%d, %d] \n", rec->pos1.xpos, rec->pos1.ypos);
	printf("pos2: [%d, %d] \n", rec->pos4.xpos, rec->pos1.ypos);
	printf("pos3: [%d, %d] \n", rec->pos1.xpos, rec->pos4.ypos);
	printf("pos4: [%d, %d] \n", rec->pos4.xpos, rec->pos4.ypos);
}

int main()
{
	Rectangle rec1 = { {1,1}, {3,4} };
	Rectangle rec2 = { {4,5}, {20,40} };

	computeArea(&rec1);
	printPoints(&rec1);
	computeArea(&rec2);
	printPoints(&rec2);
	return 0;
}
```
## 공용체(Union Type)의 정의와 의미

구조체는 여러 자료형을 한데 묶어서 메모리 공간을 할당받는 자료형이라고 한다면
공용체는 할당받은 메모리 공간을 여러 자료형의 방식으로 접근할 수 있는 자료형이다.

```c
typedef union
{
	int num;
	char str[8];
	double R;
} UnionEx
```
공용체는 기본적으로 공용체 내부에 가장 큰 자료형의 크기를 따라간다.  
위에선 double형의 크기를 따라가 `UnionEx`의 크기는 8byte가 되며  
`num`으로 `UnionEx`에 접근하면 상위 4byte를 `int`형으로 접근이 가능하며  
`str`으로 `UnionEx`에 접근하면 8byte를 `char`형의 배열로 접근 가능하다.

## 열거형(Enumerated Type)의 정의와 의미

```c
typedef enum
{
	Do=1, Re=2, Me=3, Fa=4, So=5, La=6, Ti=7;
} Scale;

void Sound(Scale sc)
{
	switch(sc)
	{
	case Do:
		puts("도"); return;
	case Re:
		puts("레"); return;
	case Me:
		puts("미"); return;
	case Fa:
		puts("파"); return;
	case So:
		puts("솔"); return;
	case La:
		puts("라"); return;
	case Ti:
		puts("시"); return;
	}
}
```

위의 열거형의 `Do=1`는 `Scale` 내부에서 `#define Do 1`와 같은 의미를 가지며
`Scale`은 Do, Re, Me, Fa, So, La, Ti 7가지의 상수들을 저장한다.

열거형은 이름있는 상수의 정의로 의미를 부여하며
Do, Re, Me와 같이 연관있는 이름을 동시에 상수로 선언하여 프로그램의 가독성을 높인다.

