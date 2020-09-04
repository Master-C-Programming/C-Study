0829 Study
------
### 자료형에 대한 이해
* 자료형 : 데이터를 표현하는 기준
    -정수형 : char, short, int ...
    -실수형 : float, double, long double...
    -> 자료형마다 표현할수 있는 바이트 크기가 다름
cf) sizeof 연산자 -> 자료형의 크기 확인 가능

### 함수(Function)
- 독립적인 모듈의 형태

* 기본적인 구성요소 : 이름, 입력, 출력, 기능

* 예시
```c
#include <stdio.h>

int Increament(int n) //함수의 이름 : Increament
{
    n++; //함수의 기능
    return n; // 함수의 출력
}

int main(void)
{
    int num = 2;

    num = Increament(num); // 함수의 입력 및 호출
    ...
    return 0;
}
```
cf) main(void) 
    - void = 빈 또는 없는
    - 함수가 호출될때 전달되는 값이 없음

* 함수내에 함수 호출 가능
  
* 선언의 경우 가급적이면 함수 밖에 둠

# code review
## leegwanh
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

<br>rewiew</br>
1. 주석다는 습관은 좋다고 생각
2. 변수명을 알기 쉽게 설정하는것이 좋았음

## son
```c
#define _CRT_SECURE_NO_WARNINGS
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

<br>rewiew</br>
1. 배열에 대한 방법을 알수 있다는게 좋았음
2. total_sec 변수를 재사용 했다는 부분이 아쉬움