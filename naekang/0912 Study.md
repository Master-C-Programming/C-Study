0905 Study
------

# Code Review (1094번)

## naekang
```c
#include <stdio.h>

#define MIN_LENGTH_X 1
#define MAX_LENGTH_X 64

int main(void)
{
   int X, i; // X변수 선언
   int stick = 0; // 출력값 초기화
   int sum = 0;

   while (1)
   {
      printf("X의 길이를 입력하시오 : ");
      scanf_s("%d", &X);

      if (X > MAX_LENGTH_X || X < MIN_LENGTH_X)
      {
         printf("X의 길이는 1이상 64이하입니다.");
      }
      else
      {
         for (i = 64; i >= 1; i /= 2);
         {
            if (i > X) {
               continue;
            }
            else if (i == X) {
               stick = 1;
               break;
            }

            
            printf("%d", stick);
         }
      }
   }
   return 0;
   
}
```

_rewiew_
1. 구현실패

## leegwanh
```c
#include <stdio.h>

int main(void)
{
    int start = 64;
    // 지민이가 원하는 막대의 길이 x 선언
    int x;
    // 막대 길이의 값들을 저장하는 배열
    int length[9999] = {0};
    int pointer = 0;

    // x값 입력 받기
    scanf("%d", &x);
    length[0] = start;

    while(1)
    {
        if(x == start)
        {
            printf("%d", 1);
            break;
        }
        
        int sum = 0;

        length[pointer] = start / 2;
        length[++pointer] = start / 2;

        for(int i = 0; i < pointer; i++)
            sum += length[i];

        if(sum > x)
        {
            length[pointer--] = 0;
        }
        else if(sum == x)
        {
            int count = 0;

            for(int i = 0; i < 9999; i++)
                if(length[i] != 0)
                    count ++;

            printf("%d", count - 1);
            break;
        }

        start /= 2;
    }

    return 0;
}
```

## son
```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

#define LIMIT_UP 64
#define LIMIT_DOWN 0

int main(void) {

   int bar_x;   // 입력 받는 막대의 길이
   int binary_bar[7] = { 0 };   // 막대의 길이를 2진수로 표현할 배열
   int mok;   // 몫 저장
   int remainder;   // 나머지 저장
   int num_of_bar = 0;   // 필요 막대의 개수를 저장
   
   // 입력 값이 0 <= X <= 64 인지를 검사하고 맞으면 통과 아니면 재입력
   while (1) {
      scanf("%d", &bar_x);
      if (LIMIT_DOWN < bar_x && bar_x <= LIMIT_UP)
         break;
      else
         printf("막대의 길이는 64보다 작거나 같은 자연수입니다.");
   }
   
   // X 값을 2진수 형태로 변환하여 binary_bar에 저장하는 반복문
   for (int i = 0; i < 7; i++) {
      mok = bar_x / 2;
      remainder = bar_x % 2;
      binary_bar[i] = remainder;
      bar_x = mok;
      if (mok == 0)
         break;
   }
   
   // 2진수의 1값들이 곧 막대의 개수
   for (int j = 0; j < 7; j++)
      num_of_bar += binary_bar[j];
   
   // 막대의 개수를 출력
   printf("%d", num_of_bar);

   return 0;
}
```

## Pilse
```c
#include <stdio.h>

int main()
{
   int X=0; 
   int cnt=0;

   scanf("%d",&X);
   for(X;X>=1;)
   {
       if(X%2==1)
       cnt++;
       X=X/2;
   }
   printf("%d",cnt);
    return 0;
    
}
```

_review_
1. 가장 간단함

# Code Review (2530번)

## naekang
```c
#include <stdio.h>

int main()
{
   int A, B, C, D;

   scanf_s("%d %d %d %d", &A, &B, &C, &D);

   C += D;
   B += C / 60;
   C %= 60;
   A += B / 60;
   B %= 60;
   A %= 24;
   

   printf("%d %d %d", A, B, C);
   return 0;
}
```

## leegwanh
```c
#include <stdio.h>

#define HOUR_UPPER_LIMIT 23
#define HOUR_LOWER_LIMIT 0

#define MINUTE_UPPER_LIMIT 59
#define MINUTE_LOWER_LIMIT 0

#define SEC_UPPER_LIMIT 59
#define SEC_LOWER_LIMIT 0

#define TIME_UPPER_LIMIT 500000
#define TIME_LOWER_LIMIT 0

int main(void)
{
    int hour, minute, sec;
    int time;
    int result_hour, result_minute, result_sec;
    int remainder;

    while(1)
    {
        printf("시, 분, 초를 입력하세요 : ");
        scanf("%d %d %d", &hour, &minute, &sec);

        if((hour < HOUR_LOWER_LIMIT || hour > HOUR_UPPER_LIMIT) ||
           (minute < MINUTE_LOWER_LIMIT || minute > MINUTE_UPPER_LIMIT) ||
           (sec < SEC_LOWER_LIMIT || sec > SEC_UPPER_LIMIT))
            printf("잘못된 입력입니다.\n\n");
        else
            break;
    }

    while(1)
    {
        printf("요리하는 데 필요한 시간을 입력하세요 : ");
        scanf("%d", &time);

        if(time > TIME_UPPER_LIMIT || time < TIME_LOWER_LIMIT)
            printf("잘못된 입력입니다.\n\n");
        else
            break;
    }

    result_hour = (time / 3600);
    remainder = time % 3600;
    result_minute = (remainder / 60);
    remainder %= 60;
    result_sec = remainder;

    if(sec + result_sec >= 60)
    {
        result_minute++;
        result_sec -= 60;
    }

    if(minute + result_minute >= 60)
    {
        result_hour++;
        result_minute -= 60;
    }
    
    if(hour + result_hour >= 24)
    {
        result_hour %= 24;
    }

    printf("%d %d %d", hour + result_hour, minute + result_minute, sec + result_sec);

    return 0;
}
```

_rewiew_
1. 구현실패

## son
```c
#define  _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

// 사용할 숫자 정의
#define ZERO 0
#define YI_SIB_SA 24
#define YUK_SIB 60
#define SAM_CHEON_YUK_BAEK 3600
#define OH_SIB_MAAN 500000

int main(void)
{
   int si;
   int buun;
   int cho;   // 시계의 시, 분, 초
   int cook_sec;   // 요리할 초
   int X;   // 계산할 때 사용할 변수

   while (1) {
      scanf("%d %d %d", &si, &buun, &cho);
      if (ZERO <= si && si < YI_SIB_SA
         && ZERO <= buun && buun < YUK_SIB
         && ZERO <= cho && cho < YUK_SIB)
         break;   // 조건에 맞을 때만 반복문 탈출
      else
         printf("시간에 맞게 다시 입력하세요!");
   }

   while (1) {
      scanf("%d", &cook_sec);
      if (ZERO <= cook_sec && cook_sec <= OH_SIB_MAAN)
         break;   // 조건에 맞을 때만 반복문 탈출
      else
         printf("시간에 맞게 다시 입력하세요!");
   }

   si += cook_sec / SAM_CHEON_YUK_BAEK;
   X = cook_sec % SAM_CHEON_YUK_BAEK;
   buun += X / YUK_SIB;
   X %= YUK_SIB;
   cho += X;
   printf("%d %d %d", si, buun, cho);

   return 0;
}
```

## Pilse
```c
#include <stdio.h>

int main()
{
    int A = 0; //현재 시
    int B = 0; //현재 분
    int C = 0; //현재 초
    int D = 0; //필요한 시간(초)

    scanf("%d %d %d", &A, &B, &C); //현재시간 입력
    scanf("%d", &D);               //필요한 시간 입력
    
    /*                                         분
        D초를 시간.분.초 로 나누는법             ㅡ
        시간 : (D/60)/60                   60 | D
        분   : (D/60)%60                       
        초   : (D%60)
    */
    C = C + (D % 60);
    if (C >= 60)
    {
        B++;
        C = C - 60;
    }
    B = B + (D / 60) % 60;
    if (B >= 60)
    {
        A++;
        B = B - 60;
    }
    A = A + (D / 60) / 60;
    while(1)    // 엄청 큰 D가 들어올경우
    {   
        if (A > 24)
            A = A - 24;
        else
            break;
    }
    printf("%d %d %d", A, B, C);

}
```