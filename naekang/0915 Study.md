0915 Study
------

### 변수의 종류에 따른 특성과 할당 위치

* 지역변수, 매개변수 : 스택 영역에 할당
  - 지역변수 : 대입연산자를 통해 초기화
  - 매개변수 : 함수호출 시 전달되는 인자값을 통해 초기화
  
* 전역변수 : 데이터 영역에 할당
  - 전역변수는 초기화하지 않으면 0으로 초기화됨
  - 전역변수는 반드시 상수로 초기화
  - 단점 : 다른 함수로부터의 잘못된 접근 가능성

* 정적 지연변수 
  - 선언은 비록 함수 안에 있지만 함수가 호출되기 전에 이미 데이터 영역에 올라감

* static변수 : 소멸되지 않고 그대로 유지하면서 하나의 함수에만 접근

* register : 지역변수인데 선언되는 크기가 작지만 호출되는 빈도수는 많을때!

<예제 1 : 저금통 함수 정의>
```c
#include <stdio.h>

void SavingBox(int money);

int main(void)
{
    SavingBox(100);
    SavingBox(150);
    SavingBox(200);
    return 0;
}

void SavingBox(int money)
{
    static int accMoney;
    accMoney += money;
    printf("누적된 금액 : %d \n", accMoney);
}
```

# printf함수와 scanf함수의 서식문자 정리

### printf함수의 기본 서식문자

|서식문자|자료형|출력형태|
|------|---|---|
|%d|int|부호있는 10진수 정수|
|%u|unsigned int|부호없는 10진수 정수|
|%o|unsigned int|부호없는 8진수 정수|
|%x, %X|unsigned int|부호없는 16진수 정수|
|%f|double|10진수 방식의 부동소수점 실수|
|%e, %E|double|e또는E 방식의 부동소수점 실수|
|%g, %G|double|값에따라 %f와 %e 사이에서 선택|
|%c|int|값에 대응하는 문자|
|%s|char*|문자열|
|%p|void*|포인터의 주소 값|
|%n|int*|포인터의 주소 값|