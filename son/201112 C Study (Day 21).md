20-11-12 C Study (Day 21)
=====
교제 : 윤성우의 열혈 C 프로그래밍

chapter 23 : 구조체와 사용자 정의 자료형2  

<hr>

## 구조체의 정의와 typedef

`int num;`과 같은 선언을 하는 것처럼 구조체 또한 `struct`없이 선언을 하고 싶다.  

### typedef 선언

`typedef int INT;`  
`typedef` 선언은 글자 그대로 type을 define한다는 의미를 가지며  
INT를 int 자료형으로 정의한다는 뜻이다.

이는 어떠한 자료형에도 사용이 가능하며 구조체 `struct` 선언도 포함된다.  

```c
struct point
{
	int xpos;
	int ypos;
};

struct point Pos;	// Pos를 point 구조체 자료형으로 정의!!
```

`typedef`에는 관례가 있는데 `typedef` 이후에 오는 자료형의 선언은 대문자로 시작하는 것이다.
이것이 `typedef`로 새롭게 정의된 자료형임을 구분할 수 있게 해준다.

typedef와 struct 선언을 합쳐 선언하는 방법도 있다.
```c
typedef struct point
{
	int xpos;
	int ypos;
} Pos;
```
이때 선언에 용이하게 `struct` 이후에 오는 `point`는 생략이 가능하다.

## 함수로의 구조체 변수 전달과 반환

함수의 매개변수로 구조체를 넘겨주면 구조체의 모든 맴버가 매개변수로 복사된다.  

### 구조체 변수를 대상으로 가능한 연산

기본 자료형 변수는 다양한 종류의 연산이 가능하나, 구조체 변수는 매우 제한된 형태의 연산만 허용된다.
허용된 연산 중 대표적인 것은 대입연산이며, 이외로 주소 값과 연관된 & 연산이나 구조체 변수의 크기를 반환하는 sizeof 연산 등이 있다.  

#### 구조체 변수의 덧셈과 뺄셈

이러한 연산들은 사용자가 직접 정의해 주어야 하며 예시는 다음과 같다.  

```c
Point AddPoint (Point pos1, Point pos2)
{
	Point pos = {pos1.xpos + pos2.xpos, pos1.ypos + pos2.ypos};
	return pos;
}

Point SubPoint Point pos1, Point pos2)
{
	Point pos = {pos1.xpos - pos2.xpos, pos1.ypos - pos2.ypos};
	return pos;
}
```

## 예제 1

예시의 point 구조체를 이용하며 두 구조체 변수를 대상으로 저장된 값을 서로 바꿔주는 함수를 정의하고 호출하는 예제를 작성해보자.

### 코드 1

```c
#include <stdio.h>

typedef struct point
{
	int xpos;
	int ypos;
} Point;

void SwapPoint (Point * point1, Point * point2)
{
	Point temp = (*point1);
	
	point1->xpos = point2->xpos;
	point1->ypos = point2->ypos;
	
	point2->xpos = temp.xpos;
	point2->ypos = temp.ypos;
}

int main()
{
	Point pos1 = {2, 4};
	Point pos2 = {5, 7};
	
	SwapPoint(&pos1, &pos2);
	
	printf("pos1 : [%d, %d] \n", pos1.xpos, pos1.ypos);
	printf("pos2 : [%d, %d] \n", pos2.xpos, pos2.ypos);
	return 0;
}
```
