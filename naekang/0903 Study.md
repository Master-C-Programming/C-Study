0903 Study
------

### while문에 의한 문장의 반복
* 기본원리 : '반복조건'이 '참'인동안 '반복의 영역'을 반복실행

<예제> Hello World 7회 반복, while문 사용
```c
#include <stdio.h>

int main()
{
    int i = 0; // 반복 횟수 카운트를 위한 변수

    while(i < 7) // 반복문 탈출 조건
    {
        printf("%d번째 : Hello World\n", i+1);
        i++; // 탈출조건 성립을 위한 증가연산
    }
    return 0;
}
```
* 중괄호를 없애려면 반복실행할 문장이 하나여야함.
  
* 무한루프의 구성 : while(1)
* 무한루프의 탈출 : break문

<예제> n회의 시도
```c
#include <stdio.h>

int main(void)
{
    int cnt = 0;
    int len = 0;

    printf("맞출 때까지 계속되는 퀴즈! \n");
    printf("한남대교의 길이는? \n");

    while(1)
    {
        cnt++;
        printf("정답? ");
        scanf("%d", &len);

        if(len == 915)
            break;
        else if(len < 915)
            printf("그보다는 길어요 \n");
        else
            printf("그보다는 짧아요 \n");
    }
    printf("정답입니다. %d번의 시도. ", cnt);
    return 0;
}
```

* continue문 : 반복문의 나머지 부분을 생략하고 조건검사 부분으로 이동

<예제> 100이하의 자연수 중 2의 배수도, 3의 배수도 아닌 자연수 출력
```c
#include <stdio.h>

int main(void)
{
    int cnt = 0;
    int n = 0;

    printf("2와 3의 배수가 아닌 자연수들\n");
    while((n++) < 100)
    {
        if(! (n % 2) || ! (n % 3))  /* if((n % 2) == 0 || (n % 3) == 0) 와 동일 */
            continue;

        printf("\n\n");
        cnt++;
    }

    printf("\n\n");
    printf("2와 3의 배수가 아닌 100 이하의 자연수 개수 : %d \n", cnt);
    return 0;
}
```

### do-while문의 이해와 활용

* while문과의 차이 : 조건검사의 위치 
    while문 : 앞쪽 , do-while문 : 뒤쪽

* 조건에 따라 더 합리적인 방법을 찾아서 사용

### for문에 의한 문장의 반복

* 반복문 구성의 3대 요소
  1. 반복 횟수를 세기 위한 변수
  2. 반복문의 탈출조건
  3. 탈출조건 성립을 위한 연산

* 세가지 구성 요소를 한번에 나타낸 구문 = for문

* 구성 : for(초기식; 조건식; 증감식) { for 문의 몸체 }
  
* 중간 구성요소가 빠지면 무한루프 