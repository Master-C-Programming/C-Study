20-09-29 C Study (Day 14)
=====
교제 : 윤성우의 열혈 C 프로그래밍

chapter 18

<hr>

### 2차원 배열의 포인터 형

2차원 배열의 포인터 형에는 2가지 정보를 갖는다.  
- 가리키는 대상
- 배열이름을 대상으로 값의 1 증감연산 시 얼마나 증감하는가

`int arr2d[3][4]`의 저 2가지 정보를 포함한 포인터 형은 다음과 같다.

`int (*ptr) [4]`  
- int형 변수를 가리키는 포인터
- 포인터 연산 시 4칸씩 건너뛴다

### 함수 인자로 전달하기

```
int main() {
	int arr1[2][6];
	double arr2[4][8];
	arr2dFunc(arr1, arr2);
	. . . .
}
```
위의 `arr2dFunc`에 `arr1`와 `arr2`의 주소 값을 인자로 넘겨주기 위해선 매개변수가 다음과 같이 선언 되어야 한다.  
`void arr2dFunc(int (*parr1)[6], double (*parr2)[8]) { . . . }`  
또는 매개변수 선언 시에만 적용할 수 있는 방법이 있는데  
`void arr2dFunc(int parr1[][6], double parr2[][8]) { . . . }`  
와도 같은 의미를 지닌다, 그러나 매개변수 이외의 블록에선 안되니 주의하자.  

#### 배열의 세로길이 계산하기

생각해보면 간단하다 배열의 전체 크기를 행의 길이로 나눠주면 된다.  
```c
#include <stdio.h>

int main() {
	int arr2d[4][9];
	printf("sizeof arr2d: %d \n", sizeof(arr2d));
	printf("sizeof row: %d \n", sizeof(arr2d[0]));
	printf("sizeof column: %d \n", sizeof(arr2d)/sizeof(arr2d[0]));
}
```

### arr[i]와 *(arr+i)

2차원 배열에서도 기본적으로 비슷하게 동작한다.  

```c
#include <stdio.h>

int main() {
	int arr2d[3][2] = {{1, 2}, {3, 4}, {5, 6}}
	printf("%p %p \n", a[2][1], (*(a+2))[1]);
	printf("%p %p \n", a[2][1], *(a[2]+1));
	printf("%p %p \n", a[2][1], *(*(a+2)+1));
}
```
위의 출력결과는 전부 `6`으로 같다.