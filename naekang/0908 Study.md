0908 Study
------

### 반복문의 중첩(Nested Loop)

* 가장 빈번하게 사용하는 것은 for문의 중첩

```c //구구단 만들기
#include <stdio.h>

int main()
{
    int i, j;
    for(i = 1; i =< 9; i++)
    {
        for(j = 1; j =< 9; j++)
        {
            printf("%d * %d = %d", i, j, i * j);
        }
    }
    return 0;
}
```

* while문의 중첩

```c //똑같은 구구단 만들기
#include <stdio.h>

int main()
{
    int i, j;

    i = 1;

    while(i++ < 10)
    {
        j = 1;
        while(j++ < 10)
        {
            printf("%d * %d = %d", i, j, i * j);
            j++;
        }

        printf("\n");
        i++;
    }
    return 0;
}
```

* break문은 자신을 감싸고 있는 하나의 반복문만 탈출함

* 코딩 연습(AB + BA = 99 를 만족하는 A, B의 조합을 구하는 프로그램)
```c
#include <stdio.h>

int Sum99(int n1, int n2);

int main()
{
    int i, j;

    for(i = 0; i < 9; i++)
    {
        for(j = 0; j < 9; j++)
        {
            if(Sum99(i, j))
                printf("[A, B] = [%d, %d] \n", i, j);
        }
    }
    return 0;
}

int Sum99(int n1, int n2)
{
    if((n1*10+n2)+(n2*10+n1) == 99)
        return 1;
    else
        return 0;
}
```

# 문자의 표현 방법과 문자 관련 표준함수들

### 문자의 표현 방법

* ex) char ch1 = 'A';

* char형 변수는 정수를 저장하는 것이 원칙이나 위와 같은 경우 아스키코드를 활용하여 문자형 저장 가능
  
* 문자의 출력 : printf("%c", ch1);

### 문자 관련 함수들

* isdigit 함수
  - 인자로 전달되는 문자가 한자리수 숫자라면 0이 아닌 값을, 숫자가 아니라면 0을 반환
  - #include문으로 헤더파일 ctype.h를 포함해야함
```c
#include <stdio.h>
#include <ctype.h>
```

* isalpha 함수
  - 알파벳이라면 0이 아닌값을, 알파벳이 아니라면 0을 반환
  - include문으로 헤더파일 ctype.h을 포함해야함
  
* islower, isupper 함수
  - 소문자, 대문자라면 0이 아닌값을, 아니라면 0을 반환
  - include문으로 헤더파일 ctype.h을 포함해야함