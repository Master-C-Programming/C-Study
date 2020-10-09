0924 Study
------

# 1차원 배열의 이해와 활용

* 성적을 계산하는 프로그램 작성하기 (3명)
```c
#include <stdio.h>

int main(void)
{
    int sc1, sc2, sc3;
    int fstscore = 0;
    int sndscore = 0;

    printf("점수 : ");
    scanf("%d", &sc1);

    if(sc1 >= fstscore)
    {
        sndscore = fstscore;
        fstscore = sc1;
    }
    else if(st1 < fstscore && sndscore)
    {
        sndscore = st1;
    }

    
}


```