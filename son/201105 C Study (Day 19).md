20-11-05 C Study (Day 19)
=====
교제 : 윤성우의 열혈 C 프로그래밍

chapter 21 : 문자와 문자열 관련 함수  

<hr>

## 문자열 관련 함수

헤더파일 `string.h`에 선언된 문자열 관련 함수들 중 유용한 몇몇 함수를 알아보자  

### 문자열 길이를 반환하는 strlen

```c
#include <string.h>
size_t strlen(const char * s);
	-> 전달된 문자열의 길이를 반환하나, 널 문자는 길이에 포함되지 않음
```

반환형인 size_t는 다음과 같이 선언되어 있다.  
`typedef unsigned int size_t`  

참고로 unsigned int 형은 printf로 출력할 때의 서식문자는 %u이나 %d로 출력해도 아무 오류없이 출력이 잘 되며 이것이 더 흔한 일이라고 한다.  

#### const char *에 대하여

앞에선 짚지 않고 넘어 갔는데 puts와 fputs의 매개변수에도 `const char *` 형의 매개변수를 보았었다. 이렇게 포인터 변수 앞에 붙은 const 선언은 `char *`포인터가 가리키는 대상을 변경하지 않겠다는 선언이다.  
이러한 선언이 필요한 이유는 해당 데이터에 접근하는 과정에서 read only로 설정하여 해당 데이터가 변경되는 상황을 막기 위함이라고 한다.

### 문자열을 복사하는 함수: strcpy, strncpy

```c
#include <string.h>
char * strcpy(char * dest, const char * src);
char * strncpy(char * dest, const char * src, size_t n);
	-> 복사된 문자열의 주소 값 반환
```

dest는 복사 받는 문자열 src는 복사의 대상이 되는 문자열이고 strncpy는 size_t n의 길이만큼 복사를 하는 함수이다.  
strncpy 함수에서 주의할 점은 복사과정에서 '널 문자'의 삽입은 따로 되지 않다는 점이다.
따라서 따로 복사된 문자열의 뒤에 '널 문자'를 삽입해 주어야 출력을 할 때 오류가 나지 않는다.

### 문자열을 덧붙이는 함수: strcat, strncat

```c
#include <string.h>
char * strcat(char * dest, const char * src);
char * strncat(char * dest, const char * src, size_t n);
	-> 덧붙여진 문자열의 주소 값 반환
```

위의 덧붙이는 함수는 dest에 src를 덧붙이는데 dest의 문자열 끝의 널 문자에 src를 덧붙인 후 널 문자를 끝에 삽입해 준다.
호기심에 배열의 index를 넘거가게 덧붙여 보았는데 널문자가 정상적으로 삽입되어 의도하지 않은 문자는 출력되지 않으나 경고 메세지를 보게된다.

### 문자열을 비교하는 함수: strcmp, strncmp

```c
#include <string.h>
int strcat(const char * s1, const char * s2);
int strncat(const char * s1, const char * s2, size_t n);
	-> 두 문자열의 내용이 같으면 0, 같지 않으면 0이 아닌 값 반환
```

여기서 0이 아닌 값을 반환 할 때 사전편산 순을 기준으로 한다.  
s1의 사전편산 순의 ASCII코드 값이 더 크면 양수를 반환하고
s1의 사전편산 순의 ASCII코드 값이 더 작으면 음수를 반환한다.  
그렇다고 명확한 값은 컴파일러마다 다르다고 하니 같은 문자열이면 0 아니면 0이 아닌 값으로 기억하면 된다.

### 문자열 변환 함수들

```c
#include <string.h>
int atoi(const char * str);		// 문자열의 내용을 int형으로 변환
long atol(const char * str);	// 문자열의 내용을 long형으로 변환
double atof(const char * str);	// 문자열의 내용을 double형으로 변환

```
상당히 유용한 함수이다.  
scanf는 상당히 메모리가 큰 함수이기에 fgets와 같은 함수를 사용하게 되는데 이 함수는 scanf와는 달리 숫자를 그대로 받아들일 수 없어 숫자를 입력 받고 싶으면 문자열을 정수형이나 실수형의 숫자로 변환하는 과정이 필요했다.  

## 프로그래밍 예제

#### 문제 1
```
적당한 길이의 문자열을 입력 받아 
그 안의 아라비아 숫자의 총합을 구하는 프로그램을 작성해 보자.
```

#### 코드 1

```c
#include <stdio.h>
#include <string.h>

int main(void) 
{
	char str[20];;
	int strSum = 0;
	int cmp;

	gets(str);

	for (int i = 0; i < strlen(str); i++) 
	{
		cmp = str[i] - '0';
		if (0 <= cmp && cmp <= 9) 
		{
			strSum += cmp;
		}
	}

	printf("문자열 중 아라비아 숫자의 총 합: %d", strSum);

	return 0;
}
```

#### 문제 2
```
이름과 나이를 입력받는 프로그램을 작성하고 
이름과 나이가 각각 같은지 다른지 판단하여 출력하는 프로그램을 작성해 보자

입력의 예시는 다음과 같고 이름과 나이 사이에만 공백이 삽입되어야 한다.
"이정신 29"
"한수정 7"
"오선주 17"
```

#### 코드 2

```c
#include <stdio.h>
#include <string.h>

// 공백의 index를 찾아주는 함수
int find_spaceIndex(const char* s) 
{
	for (int i = 0; i < strlen(s); i++)
	{
		if (s[i] == ' ')
			return i;
	}
	// 공백을 찾지 못했을 경우 -1 리턴
	return -1;
}

int main(void) 
{
	char str1[20];
	char str2[20];
	int temp1;
	int temp2;

	fgets(str1, strlen(str1), stdin);
	fgets(str2, strlen(str2), stdin);

	// 공백이 들어간 index를 각각 저장
	temp1 = find_spaceIndex(str1);
	temp2 = find_spaceIndex(str2);

	if (temp1 == -1 || temp2 == -1)
	{
		printf("공백을 정확히 입력하시오.");
		return 0;
	}

	// 공백이 들어간 index + 1 부터 문자열 비교
	// strcmp의 리턴 값은 문자열이 같을 때 0, 이외는 0이 아닌 수
	if (strcmp((str1 + temp1 + 1), (str2 + temp2 + 1)))
		printf("나이가 다릅니다. \n");
	else
		printf("나이가 같습니다. \n");

	// temp끼리 다르면 이름이 다른 것
	if (temp1 == temp2)
	{
		// temp까지의 문자열 비교
		if (strncmp(str1, str2, temp1))
			printf("이름이 다릅니다. \n");
		else
			printf("이름이 같습니다. \n");
	}
	else
		printf("이름이 다릅니다. \n");

	return 0;
}
```