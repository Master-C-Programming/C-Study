# 0905 C-Study

###### Baekjoon online judge 5543번 문제 풀이 & 코드 공유 & 리뷰
<hr>

* __문제__<br>
    상근날드에서 가장 잘 팔리는 메뉴는 세트 메뉴이다. 주문할 때, 자신이 원하는 햄버거와 음료를 하나씩 골라, 세트로 구매하면, 가격의 합계에서     50원을 뺀 가격이 세트 메뉴의 가격이 된다.
    햄버거는 총 3종류 상덕버거, 중덕버거, 하덕버거가 있고, 음료는 콜라와 사이다 두 종류가 있다.
    햄버거와 음료의 가격이 주어졌을 때, 가장 싼 세트 메뉴의 가격을 출력하는 프로그램을 작성하시오.

* __입력__<br>
    입력은 총 다섯 줄이다. 첫째 줄에는 상덕버거, 둘째 줄에는 중덕버거, 셋째 줄에는 하덕버거의 가격이 주어진다. 넷째 줄에는 콜라의 가격, 다섯째 줄에는 사이다의 가격이 주어진다. 모든 가격은 100원 이상, 2000원 이하이다.

* __출력__<br>
    첫째 줄에 가장 싼 세트 메뉴의 가격을 출력한다.
<hr>

### leegwanh

```c
#include <stdio.h>

#define LOWER_LIMIT_PRICE 100
#define UPPER_LIMIT_PRICE 2000
#define DISCOUNT 50

int main(void)
{
    // 버거 변수 3개 선언
    int burger_1, burger_2, burger_3;
    // 음료 변수 2개 선언
    int drink_1, drink_2;

    // 올바른 입력이 들어오면 반복문 종료
    while(1)
    {
        printf("3가지 버거와 2가지 음료의 가격을 차례대로 입력하세요.\n");
        scanf("%d %d %d %d %d", &burger_1, &burger_2, &burger_3, &drink_1, &drink_2);

        if((burger_1 < LOWER_LIMIT_PRICE || burger_1 > UPPER_LIMIT_PRICE) ||
           (burger_2 < LOWER_LIMIT_PRICE || burger_2 > UPPER_LIMIT_PRICE) ||
           (burger_3 < LOWER_LIMIT_PRICE || burger_3 > UPPER_LIMIT_PRICE) ||
           (drink_1 < LOWER_LIMIT_PRICE || drink_1 > UPPER_LIMIT_PRICE) ||
           (drink_2 < LOWER_LIMIT_PRICE || drink_2 > UPPER_LIMIT_PRICE))
        {
            // 값이 범위를 벗어난다면 이 부분 실행
            printf("모든 가격은 %d원 이상, %d원 이하입니다.", LOWER_LIMIT_PRICE, UPPER_LIMIT_PRICE);
        }
        else
        {
            // 값이 정상범위라면 이 부분 실행
            // 가격이 가장 싼 버거와 음료의 값을 저장하는 변수 선언
            int burger, drink;

            // 가격이 제일 싼 버거를 burger에 저장
            burger = burger_1 < burger_2 ? burger_1 : burger_2;
            burger = burger < burger_3 ? burger : burger_3;

            // 가격이 제일 싼 음료를 drink에 저장
            drink = drink_1 < drink_2 ? drink_1 : drink_2;

            // 세트 가격 출력
            printf("%d", (burger + drink) - DISCOUNT);

            //루프 탈출
            break;
        }
    }

    // 프로그램 종료.
    return 0;
}
```

### naekang

```c
#include <stdio.h>

#define LOWER_LIMIT_TOP 100
#define UPPER_LIMIT_TOP 2000
#define LOWER_LIMIT_MIDDLE 100
#define UPPER_LIMIT_MIDDLE 2000
#define LOWER_LIMIT_BOTTOM 100
#define UPPER_LIMIT_BOTTOM 2000
#define LOWER_LIMIT_COKE 100
#define UPPER_LIMIT_COKE 2000
#define LOWER_LIMIT_SODA 100
#define UPPER_LIMIT_SODA 2000

int main()
{
   int TOP, MIDDLE, BOTTOM; // 버거 변수 정의
   int COKE, SODA; // 음료 변수 정의
   int CHEAP_BURGER, CHEAP_DRINK; // 가장 저렴한 버거와 음료 정의

   scanf_s("%d %d %d %d %d", &TOP, &MIDDLE, &BOTTOM, &COKE, &SODA); // 첫 줄에 다섯개의 변수를 입력 받음

   if (TOP < MIDDLE && TOP < BOTTOM) { // 상덕버거가 가장 싼 경우
      CHEAP_BURGER = TOP;
   }
   else if (MIDDLE < TOP && MIDDLE < BOTTOM) { // 중덕버거가 가장 싼 경우
      CHEAP_BURGER = MIDDLE;
   }
   else { // 하덕버거가 가장 싼 경우
      CHEAP_BURGER = BOTTOM;
   }

   if (COKE < SODA) { // 콜라가 싼 경우
      CHEAP_DRINK = COKE;
   }
   else // 사이다가 싼 경우
      CHEAP_DRINK = SODA;

   printf("%d", CHEAP_BURGER + CHEAP_DRINK - 50); // 세트메뉴의 가격 = 가장 싼 버거 + 가장 싼 음료 - 50
   return 0;
}
```

### son

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

#define LOWER_LIMIT 100
#define UPPER_LIMIT 2000

int main(void) {

   int DuckBurger[3];   // 버거의 가격을 입력 받는 배열
   int Beverage[2];   // 음료의 가격을 입력 받는 배열
   int CheapBurger = 2001;   // 2000보다 크게 초기화 하여 이후 가장 싼 버거의 가격 값을 담음
   int CheapBeverage = 2001; // 가장 싼 음료의 가격을 담는 변수

   for (int i = 0; i < 3; i++) {
      scanf("%d", DuckBurger + i);// 버거 값 입력
      if (DuckBurger[i] < LOWER_LIMIT || DuckBurger[i] > UPPER_LIMIT) {   // 100 <= 버거가격 <= 2000 일때만 입력받게 만듦
         printf("버거의 가격은 100이상, 2000이하로 설정해주세요! \n %d \n", i);
         i--;   // 다시 재입력을 위한 반복인자 값 감소
         continue;   // 반복문 처음으로 돌아가 다시 입력을 받음
      }
      if (CheapBurger > DuckBurger[i])
         CheapBurger = DuckBurger[i];   // 첫번째 배열의 인자를 무조건 담아 계속 비교하여 작은 값을 담는다
   }
   for (int j = 0; j < 2; j++) {
      scanf("%d",Beverage+j);   // 음료 값 입력
      if (Beverage[j] < LOWER_LIMIT || Beverage[j] > UPPER_LIMIT) {
         printf("음료의 가격은 100이상, 2000이하로 설정해주세요! \n %d \n", j);
         j--;
         continue;
      }
      if (CheapBeverage > Beverage[j])
         CheapBeverage = Beverage[j];
   }
   printf("%d", CheapBurger + CheapBeverage - 50 );   // 가장 싼 버거와 음료의 값을 더하여 50원을 할인해준다
   return 0;
}
```

##### 솔직담백 Review
- `naekang`의 코드에서는, define으로 정의한 상수(문제 조건)을 실제 코드에서 사용하지 않았다. 웬만하면 상수는 대문자로, 변수는 소문자로 작성하여 구분이 용이하게 하자. 만약 TOP, MIDDLE의 가격이 같고 BOTTOM의 값이 제일 비싸다면, else문이 실행될텐데, 그렇다면 이것은 오류가 된다. if, else if 조건문에 등호를 넣도록 하자. <br>

- `son`의 코드에서는, operator와 operands사이 공백을 넣을 건지 뺄 건지 확실히 정해서, 코드의 통일성을 유지하자. <br>

- `leegwanh`의 코드에서는 삼항연산자를 사용하였다. 비교적 간단하게 최소 가격을 구할 수 있다. <br>

- 주석의 위치? <br>
주석을 옆에 달 건지, 위에 달 건지? <br>
    * 옆으로 <br>
    옆에 달면 옆으로 길어져 보기 좀 안 좋다. 그러나 위로 달았을 때와 비교해보면 코드의 길이가 더 짧고 간결해보인다.
    * 위로<br>
    코드가 옆으로 길어지지 않고, 코드를 차례대로 읽어나가면서 자연스럽게 주석을 볼 수 있다. 그러나 코드의 길이가 길어지며 난잡해보일 수 있다.


