20-10-06 C Study (Day 16)
=====
교제 : 윤성우의 열혈 C 프로그래밍

chapter 19

<hr>

## main 함수로의 인자전달

main함수도 함수라 반환형과 매개변수가 존재하는데 과연 어떻게 작동할까?  

`int main(int argc, char * argv[]) { . . . }`  
다음과 같이 main함수를 정의할 수 있다.  

```c
#include <stdio.h>

int main(int argc, char* argv[]) {
	int i = 0;
	printf("전달된 문자열의 수: %d \n", argc);

	for (i = 0; i < argc; i++)
		printf("%d번째 문자열: %s \n", i+1, argv[i]);
	return 0;
}
```
다음과 같이 main함수를 작성하고 실행파일인 exe가 들어 있는 파일을 명령 프롬프트로 띄워보자  
(프로젝트명은 Maintest이다.)  
```
C:\Users\~~~~~ >cd source\repos\Maintest\Debug

C:\Users\~~~~~\source\repos\Maintest\Debug>Maintest I like you
전달된 문자열의 수: 4
1번째 문자열: Maintest
2번째 문자열: I
3번째 문자열: like
4번째 문자열: you
```
cmd에 다음과 같이 입력하면 결과가 출력된다.  

`char* argv[]`는 char형 포인터 배열이다.

|배열 요소|  전달 인자   | 
|---------|--------------|
|strArr[0]|Maintest\0|
|strArr[1]|I\0|
|strArr[2]|like\0|
|strArr[3]|you\0|
|strArr[4]|NULL|

위와 같이 strArr 배열이 만들어져  
main(4, strArr)와 같이 main 함수가 호출된다. 

```c
#include <stdio.h>

int main(int argc, char* argv[]) {
	int i = 0;
	printf("전달된 문자열의 수: %d \n", argc);

	while(argv[i] != NULL) {
		printf("%d번째 문자열: %s \n", i+1, argv[i]);
		i++;
	}
	return 0;
}
```
다음과 같이 작성하여 strArr의 마지막 인자로 NULL값이 들어가는 것을 확인할 수 있다.  
