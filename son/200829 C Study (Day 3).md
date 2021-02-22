20-08-29 C Study (Day 3)
=======
### 코드 실습 및 리뷰 (1주차)

##### 실습문제 : Backjoon [5554번](https://www.acmicpc.net/problem/5554)

<hr>

### leegwanh

```c
#include <stdio.h>

#define LOWER_LIMIT_SECOND 60
#define UPPER_LIMIT_SECOND 3599

int main(void)
{
    //변수 설정
    int home_to_school;
    int school_to_pc;
    int pc_to_academy;
    int academy_to_home;
    int sum;

    //이동시간 조건 불만족 시 계속 입력 반복
    while(1)
    {
        //이동시간 입력 받기
        printf("집에서 학교까지의 이동시간을 적으세요(단위 : sec) : ");
        scanf("%d", &home_to_school);
        printf("학교에서 PC방까지의 이동시간을 적으세요(단위 : sec) : ");
        scanf("%d", &school_to_pc);
        printf("PC방에서 학원까지의 이동시간을 적으세요(단위 : sec) : ");
        scanf("%d", &pc_to_academy);
        printf("학원에서 집까지의 이동시간을 적으세요(단위 : sec) : ");
        scanf("%d", &academy_to_home);

        //이동시간 총합 구하기
        sum = home_to_school + school_to_pc + pc_to_academy + academy_to_home;
        //이동시간 조건 검사
        if(sum < LOWER_LIMIT_SECOND)
        {
            //이동시간이 하한선보다 낮다면 이 부분 실행
            printf("\n이동시간이 비현실적입니다!!\n");
            //재입력 받음
            printf("이동시간을 다시 작성합니다.\n\n");
        }
        else if(sum > UPPER_LIMIT_SECOND)
        {
            //이동시간이 상한선보다 높다면 이 부분 실행
            printf("\n축하드립니다! 사랑의 매를 온몸으로 받으시겠군요!!\n");
            //재입력 받음
            printf("이동시간을 다시 작성합니다.\n\n");
        }
        else
        {
            //이동시간이 정상범위라면 이 부분 실행
            printf("\n이동시간은 %d분 %d초 입니다!", (sum / 60), (sum % 60));
            //루프 탈출
            break;
        }
    }

    //프로그램 종료.
    return 0;
}
```

### naekang

```c
#include <stdio.h>

int main(void)
{
   int A=0, B=0, C=0, D = 0;
   int x, y;


   scanf_s("%d %d %d %d", &A, &B, &C, &D);

   x = (A + B + C + D) / 60;
   y = (A + B + C + D) % 60;

   printf("%d\n", x);
   printf("%d\n", y);

   return 0;
}
```

### son

```c
#include <stdio.h>

int main(void) {
   int move[4];
   int total_sec = 0, total_min = 0;

   for (int i = 0; i < 4; i++) {
      scanf("%d", move+i);
      total_sec += move[i];
   }
   if (total_sec < 60) {
      printf("시간이 너무 짧습니다!");
      return 0;
   }
   else if(total_sec > 3600){
      printf("너무 늦게 들어왔습니다!");
      return 0;
   }
   else {
      total_min = total_sec / 60;
      total_sec = total_sec % 60;
      printf("%d\n", total_min);
      printf("%d", total_sec);
   }
   return 0;
}
```

#### feedback

- 변수 선언시 한눈에 보기 좋게 선언
- 변수 선언시 초기화하는 습관 들이기
- 변수는 변수명만으로 사용용도를 알 수 있어야 하며 또한 그에 맞게 사용해야 한다.
- 주석의 중요성
- 가급적 상수는 변수에 넣어서 사용 할 것
- 코드 작성시 전체적으로 통일감 있게 정리 하자
- 