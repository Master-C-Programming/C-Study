1008 Study
------

# 1차원 char형 배열을 이용한 문자열의 표현

### 문자열 상수와 문자열 변수

||이름의 존재여부|메모리 공간 할당여부|데이터 변경 가능여부|
|---|---|---|---|
|변수|존재한다.|할당이 이뤄진다.|변경 가능하다.|
|상수|존재하지 않는다.|할당이 이뤄진다.|변경 불가능하다.|

### 문자열 변수 만들기

* char형 배열을 활용하기 : char str[5] = "ABCD"; -> A B C D \0

예제 18-2)
```c
#include <stdio.h>

int main(void)
{
    char str1[5] = "AAA";
    char str2[ ] = "BBB";
    char str3[ ] = {'A', 'B', 'C'};
    char str4[ ] = {'A', 'B', 'C', '\0'};

    printf("%s \n", str1);
    printf("%s \n", str2);
    pritnf("%s \n", str3);
    pritnf("%s \n", str4);

    str1[0] = 'C';
    str1[1] = 'B';
    pritnf("%s \n", str1);
    return 0;
}
```

실행결과)
```
AAA
BBB
ABCw$?C?|?
ABC
CBA
```

* str3의 경우 NULL값 출력

### 문자열을 입력받기 위한 scanf함수 호출문의 구성

```c
#include <stdio.h>

int main()
{
    char str[30];
    printf("문자열 입력 : ");
    scanf("%s", str);
    printf("입력받은 문자열 : %s \n", str);
    return 0;
}
```

```
문자열 입력 : KimJinHo
입력받은 문자열 : KimJinHo
```

* scanf함수 안의 str 앞에 & 연산자를 붙이지 않는 이유
 -  입력받은 값을 저장할 변수의 시작 주소를 알리기 위함

<예제 : 사용자로 부터 문자열을 입력받고 역순으로 출력하는 프로그램 작성하기>
```c
#include <stdio.h>

int main()
{
    char str[100];
    int len = 0, i;

    printf("문자열 입력 : ");
    scanf("%s", str);

    while(str[len] != '\0');
        len++;

    printf("역순출력 : ");
    for(i=len; i>0; i--)
        printf("%c", str[i-1]);
    
    return 0;
}
```