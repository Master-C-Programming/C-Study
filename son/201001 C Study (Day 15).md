20-10-01 C Study (Day 15)
=====
교제 : 윤성우의 열혈 C 프로그래밍

chapter 19

<hr>

## 함수 포인터

코드의 모든 부분은 메모리 공간에 저장된다.  
함수도 예외가 아니다 함수 또한 메모리 공간에 2진수 형태로 메모리 공간에 저장되어 호출시 실행이 된다.  
그렇다면 메모리 공간에 저장된 주소 값을 저장하는 포인터가 있을 것이다.  
이게 바로 함수 포인터이다.  

### 선언 방법

포인터에는 해당 주소에 들어있는 값을 활용하기 위한 정보가 필요하다.  
예를 들자면 int형 포인터인 경우와 double형 포인터는 값을 넘겨주면 저장하는 방식이 다르기에 반드시 정보가 필요하다.  

함수 포인터에는 다음과 같은 정보를 필요로 한다.
- 반환형
- 매개변수의 선언형태

예시로 반환형이 double이고 매개변수로 double형 1개, int형 1개의 인자를 갖는 함수 포인터를 보자  
`double (*fptr) (double, int);`  

#### 활용

```c
#include <stdio.h>

// 덧셈과 곱셈 선택 함수
int PlusOrMult (int num1, int num2, int (*cmp)(int n1, int n2)) {
	return cmp(num1, num2);
}

int PlusFunc (int num1, int num2) {
	return num1 + num2;
}

int MultFunc (int num1, int num2) {
	return num1 * num2;
}

int main(void) {
	
	int a, b, c;
	int result;
	printf("더하거나 곱할 두 값을 입력 : ");
	scanf("%d %d", &a, &b);
	printf("연산 선택 \n 덧셈 : 0 곱셈 : 1\n");
	scanf("%d", &c);
	
	// c 값에 따라 덧셈, 곱셈을 선택
	if (c == 0)
		result = PlusOrMult(a, b, PlusFunc); // 덧셈 함수를 매개변수로 전달
	else if (c == 1)
		result = PlusOrMult(a, b, MultFunc); // 곱셈 함수를 매개변수로 전달
	else {
		printf("잘못 입력 하셨습니다.");	// 잘못 입력시 프로그램 종료
		return 0;
	}
	printf("연산 결과 : %d", result); // 결과 출력
	
	return 0;
}
```
이렇게 함수를 골라 쓰는 것으로 활용 할 수도 있다.  

### void 포인터

형이 존재하지 않는 포인터를 void 포인터라고 한다.  
`void *ptr;`  

void 포인터에는 무엇이든지 담을 수 있으나 이 포인터 하나만 가지고는 아무런 연산을 할 수 없다.  
후에 메모리의 동적 할당에 깊은 관계가 있다고 하니 이후에 더 깊게 배우도록 하자.  