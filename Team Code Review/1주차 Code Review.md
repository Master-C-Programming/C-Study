# 20-08-29 1주차 C-Study Code Review

###### Baekjoon online judge 5554번 문제 풀이 & 코드 공유 & 리뷰
<hr>

* __문제__<br>
   승균이는 매일 학교, PC방, 학원에 다닌다. 반복되는 일상에 익숙해진 승균이는 이동시간을 단축해서 PC방에 더 오래 머물고 싶었다. 그래서 스톱워치를 들고 이동할 때마다 기록을 잰 후 집에 가서 분석해보기로 했다.<br>
   집에 도착한 승균이는 측정한 결과를 보는 데, 전부 초 단위로 기록되어있다! 맨날 놀기만 해서 총 이동 시간이 몇 분 몇 초인지 계산을 못 하는 승균이를 도와주자.<br>
   하루 동안 측정한 결과가 주어지면, 이날의 총 이동 시간이 몇 분 몇 초인지 출력하는 프로그램을 작성하시오.<br>

* __입력__<br>
   입력은 총 4줄이며, 한 줄에 하나씩 양의 정수가 적혀있다.<br>
   첫 번째 줄에 집에서 학교까지의 이동 시간을 나타내는 초가 주어진다.<br>
   두 번째 줄에 학교에서 PC방까지의 이동 시간을 나타내는 초가 주어진다.<br>
   세 번째 줄에 PC방에서 학원까지의 이동 시간을 나타내는 초가 주어진다.<br>
   마지막 줄에 학원에서 집까지의 이동 시간을 나타내는 초가 주어진다.<br>
   집에 늦게 가면 혼나기 때문에, 총 이동시간은 항상 1 분 0 초 이상 59 분 59 초 이하이다.<br>

* __출력__<br>
   총 이동시간 x 분 y 초를 출력한다. 첫 번째 줄에 x를, 두 번째 줄에 y를 출력한다.
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

#### review
1. 변수를 선언시에 초기화하는 습관을 들이자.
	- 쓰레기 값으로 초기화되는 일을 방지하고자 습관을 들여 놓을 것.
2. 주석을 다는 습관이 좋다.
	- 추후에 협업을 할 시에 아예 모르는 사람이 본다는 생각으로 주석을 친절하게 달 것.

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

#### review
1. 변수명을 의미있게 선언하자.
	- 변수명만 보고도 이게 어떻게 사용되는지 짐작이 되는 것이 좋다.
2. 변수 선언시에 각각 1줄씩에 선언하자.
	- 변수 선언시에 한 줄에 선언하면 한눈에 몇개의 변수가 쓰였는지 어떤 변수가 있는지 보기 어려움.
	- 변수 선언시에 보기도 좋게 띄어쓰기도 신경써 통일감있게 선언 할 것.

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

#### review
1. 변수를 변수명에 맞게 사용 할 것.
	- 변수의 개수를 줄이려는 시도는 좋으나 재활용하여 변수명과 어울리지 않는 값은 어울리지 않는다.
2. 자주사용 될 상수는 변수에 넣어서 사용하자.
	- Refactoring (코드 유지, 관리, 보수적 측면)에 유리함.
3. 중괄호를 올려쓰던 내려쓰던 통일성있게 사용하자.
	- 객체지향적 측면과 절차지향적 측면에서 다르게 사용된다고하는데 통일성만 지키면 문제되지 않을 것이다.
