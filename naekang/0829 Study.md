0828 Study
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

