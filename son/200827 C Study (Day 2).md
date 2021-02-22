20-08-27 C Study (Day 2)
=============
#### 교제 : 윤성우의 열혈 C 프로그래밍
##### ~ chapter 14 : 포인터와 함수에 대한 이해
***
### 함수의 인자로 배열 전달해보자

앞서 배열은 포인터와 연관이 있다고 배웠다 이를 통해 포인터 형으로 선언하면 되지 않을까 유추가 가능하다.

* int Function1(int* arr) { ...}
* int Function2(int arr[]) { ... }

이렇게 배열의 주소 값을 전달하면 배열의 요소에 순차적으로 접근이 가능해진다.
매개변수를 선언할 때 배열임을 쉽게 알기 위해 (int* arr)는 (int arr[])로 쓰일 수 있다.

### Call-by-value vs. Call-by-reference

쉽게 말하면 value는 값의 전달이고 reference는 주소 값의 전달이다. \
그렇다면 무슨 차이가 있을까?

두 변수의 값을 교환하는 함수를 예로 들어보자.

``` c
#include <stdio.h>

void Swap(int n1, int n2){
	int temp=n1;
	n1=n2;
	n2=temp;
}
int main(void){
	int num1=10;
	int num2=20;
	printf("num1 num2: %d %d \n",num1, num2);
	
	Swap(num1,num2);	// num1과 num2의 값이 바뀌길 기대
	printf("num1 num2: %d %d \n",num1, num2);
	return 0;
}
```

Swap함수를 호출 할시에 지역변수 n1와 n2가 할당되어 값이 temp를 통해 교환된 뒤에 Swap함수 종료시에 n1과 n2는 메모리 공간상에서 소멸된다. \
__즉, main함수의 num1과 num2에 전혀 영향을 미칠 수가 없는 것이다.__

``` c
#include <stdio.h>

void Swap(int* ptr1, int* ptr2){ // 매개 변수가 포인터 변수로 바뀜
	int temp = *ptr1;
	*ptr1 = *ptr2;
	*ptr2 = temp;
}
int main(void){
	int num1=10;
	int num2=20;
	printf("num1 num2: %d %d \n",num1, num2);
	
	Swap(&num1,&num2);	// 주소 값 전달
	printf("num1 num2: %d %d \n",num1, num2);
	return 0;
}
```
이와 같은 방식으로 num1과 num2의 주소 값을 전달하여 num1과 num2의 값에 함수 외부에서도 관여 할 수 있다. \
확장하면 scanf 함수호출 시에도 &연산자를 일반 변수앞에 붙이고 포인터형 변수에는 안 붙이는 이유를 알 수 있다.

