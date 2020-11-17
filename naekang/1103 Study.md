# 1103 Study

<u>교재 : DO it! C언어 입문</u>

------

## 12-2 문자열

### 배열로 문자열 표현하기
* char형 사용
* char data[6] = {'h','a','p','p','y',0};
* 문자열 표현을 위해 ""사용 -> 5바이트 + NULL문자 0

- 1분퀴즈)
```c
#include <stdio.h>

int main()
{
    char data_1[] = "Don't worry, Be happy!";
    char data_2[] = "걱정 마. 행복할 거야.";

    printf("%s\n", data_1);
    printf("%s\n", data_2);
    return 0;
}
```

- 배열에 저장된 문자열의 길이를 구하는 함수
```c
#include <stdio.h>

int GetStringLength(char data[])
{
    int count = 0; // 0이 나올때까지 문자의 개수를 더함
    while(data[count]) count++; // while(data[count] != 0) count++와 같은 의미
    return count;
}

int main()
{
    int data_length; // 문자열 길이를 저장할 변수
    char data[10] = {'h','a','p','p','y',0};
    data_length = GetStringLength(data);
    printf("data length = %d\n", data_length);
}
```

### 문자열을 다루는 C 내장 함수

* 문자열의 길이를 구하는 내장 함수 strlen

* 문자열을 복사하고 추가하는 내장 함수 strcpy, strcat
```c
#include <stdio.h>
#include <string.h>

int main()
{
    char data[10] = {'a', 'b', 'c', 0,}; // "abc"문자열 저장
    char result[16]; // 새로운 문자열을 저장할 변수

    strcpy(result, data); // data에 저장된 문자열을 result로 복사
    strcat(result, "def"); // result 값의 맨뒤에 "def"를 덧붙임

    printf("%s + \"def\" = %s\n", data, result);
    return 0;
}
```

## 12-3 2차원 배열

### 2차원 배열 선언하기
* char data[5][4]; // char 형식의 1차원배열 5개를 묶어 2차원 배열로 선언
  - 연산자 우선순위( [ ]연산자는 동일한 우선순위일 경우 왼쪽에서 오른쪽으로 연산수행)
  - = char(data[5])[4]; 