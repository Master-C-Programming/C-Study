# 1105 Study
------

## 12-3 2차원 배열

### 2차원 배열 선언하기
* char data[5][4]; // char 형식의 1차원배열 5개를 묶어 2차원 배열로 선언
  - 연산자 우선순위( [ ]연산자는 동일한 우선순위일 경우 왼쪽에서 오른쪽으로 연산수행)
  - = char(data[5])[4]; 
  - char data[5][4]; 
        -> 행 : data[0][0]~data[4][0] 5행 / 열 : data[0][0]~data[0][3] 4열

cf) 2차원 배열에서 행과 열 중 처리의 우선순위
* 행을 기준으로 묶는 방법을 더 많이 사용

### 2차원 배열 초기화하기
```
char temp1[3] = {1,2,3};
char temp2[3] = {4,5,6};
------------------------
char temp[2][3] = {{1,2,3},{4,5,6}};
```

cf)
* test[a] 항목과 temp[a/N][a%N] 항목은 위치가 같다.
* temp[b][c] 항목과 test[b*N+c] 항목은 위치가 같다.

### 1차원 배열과 2차원 배열의 차이
```c
#include <stdio.h>

int main(void)
{
    char data[12] = {0,0,2,0,1,1,0,0,2,1,0,2};
    int i, x, y;

    for(i = 0; i < 12; i++) {
        x = i % 4 + 1;
        y = i / 4 + 1;
        printf("%d행 %d열에", y, x);
        if(data[i] == 1) 
            printf("검은돌이 놓여 있습니다.\n");
        else if(data[i] == 2)
            printf("흰 돌이 놓여 있습니다.\n");
        else 
            printf("는 돌이 놓여있지 않습니다.\n"); 
    }
}
```

```c
#include <stdio.h>

int main(void)
{
    char data[3][4] = {{0,0,2,0}, {1,1,0,0}, {2,1,0,2}};
    int x, y;

    for(y = 0; y < 3; y++) {
        for(x = 0; x < 4; x++) {
            printf("%d행 %d열에", y+1, x+1);
            if(data[y][x] == 1)
                printf("검은돌이 놓여 있습니다.\n");
            else if(data[y][x] == 2)
                printf("흰 돌이 놓여 있습니다.\n");
            else
                printf("는 돌이 놓여있지 않습니다.");
        }
    }
}
```
- 2차원 배열이 1차원 배열보다 행, 열의 구분이 잘되어있다.

예제) 정수를 오름차순으로 정렬하기
```c
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>

int main(void)
{
    int data[7] = { 6,3,9,7,2,4,1 };
    int temp, i, j;
    
    printf("정렬전의 숫자 : ");
    for (i = 0; i < 7; i++)
        printf("%d", data[i]);

    for (i = 0; i < 7; i++) {
        for (j = i + 1; j < 7; j++) {
            if (data[i] > data[j]) {
                temp = data[i];
                data[i] = data[j];
                data[j] = temp;
            }
        }
    }
    printf("\n정렬 후 : ");
    for (i = 0; i < 7; i++)
        printf("%d", data[i]);

    return 0;
}
```