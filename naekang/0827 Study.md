2020-08-27 C-Study
=============

* 공부방법 : 인프런 c언어 강의 및 백준 단계별 문제풀이

* 공부시간 : 14:30 ~ 15:30

* 공부범위 : ~ 입출력 기본

### c언어 기본 구문
* #include <stdio.h>
* int main(void)
* { 
*   printf("Hello World!\n");     
* }

### scanf 구문 활용하기
* 정수형 -> scanf("%d", &A); printf("%d", A);
* 실수형 -> %f, 단일문자 -> %c, 문자열 -> %s

#### 백준 문제 2588번 c언어로 코딩하기
#include <stdio.h>

int main(void)
{
	int A, B;
	scanf_s("%d %d", &A, &B);
	int out1 = ((B % 100) % 10) * A;
	int out2 = ((B % 100) / 10) * A;
	int out3 = (B / 100) * A;

	printf("%d\n", out1);
	printf("%d\n", out2);
	printf("%d\n", out3);
	printf("%d\n", A * B);
	return 0;
}
