1105 study<br><br>

## 조건부 컴파일
<hr>

**`C`** 는 다양한 운영체제에서 사용되었기 때문에 각 운영체제가 제공하는 표준 함수나 그 동작이 조금씩 다를 수 있다. 같은 운영체제를 사용한다 하더라도 사용하는 컴파일러와 라이브러리에 따라서 일부 함수가 없는 경우도 있을 수 있다. 예를 들어 `Visual Studio`에서 지원하는 몇몇 함수는 `gcc`에서는 지원하지 않는다. 이런 경우 소크 코드를 따로 작성하게 되면 나중에 유지보수가 상당히 어려워진다.
<br>

이러한 문제점을 해결하기우해 존재하는 것이 조건부 컴파일이다. 이는 특정 조건에 만족할 때만 코드가 컴파일되게 한다. 조건부 컴파일은 주로 매크로 상수의 존재유무 또는 매크로 상수값을 검사하여 수행한다. 조건에따라 특정 코드를 컴파일하도록 만들수 있어서 보다 이식성 있는 코드를 개발하는데 도움이 된다.
<br>

조건부 컴파일에 사용되는 전처리기 지시자는 `#if` `#elif` `#else` `#endif` `ifdef` `ifnedf` 등이 있다.
<hr>

### `#if` ~ `#elif` ~ `else` `#endif`
<br>

조건에 만족하는지 아닌지를 검사하여 컴파일 할 문장을 `#if` ~ `#elif` ~ `else` `#endif`로 묶어준다. `#elif` 는 조건문의 `elseif` 와 같다.

```c
#include <stdio.h>

#define CODE 3

int main()
{
    double num1=3.3,num2=1.1;
    double result=0.0;

    #if(CODE<0)
        result=num1+num2;
    printf("덧셈 결과 : %lf \n",result);
    #elif(CODE==1)
        result=num1/num2;
    printf("나눗셈 결과 : %lf \n",result);
    #elif(CODE==2)
        result=num1*num2;
    printf("곱셈 결과 : %lf \n",result);
    #elif(CODE==3)
        result=num1-num2;
    printf("뺄셈 결과 : %lf \n",result);
    #else
        printf("프로그램 종료 \n");

    #endif

    return 0;

}
```
3행에서 매크로 상수 `CODE`를 3으로 정의하였기 때문에 22행부터 24행까지만 컴파일이된다. 따라서 출력값은 다음과 같다.
>뺄셈 결과 : 2.20000


<hr>

### `#ifdef` ~ `#endif` 와 `#ifndef` ~ `#endif`
<br>
                               
`#ifdef` ~ `#endif` 는 매크로가 정의되어 있느냐를 판단하여 컴파일한다.
```c
#include <stdio.h>
#define ADD
#define MUL

int main()
{
    double num1=3.3, num2=1.1;
    double result=0.0;

    #ifdef ADD
        result=num1+num2;
        printf("ADD결과 : %lf\n",result);
    #endif
    #ifdef MUL
        result=num1*num2;
        printf("MUL결과 : %lf\n",result);
    #endif

    return 0;
}
```
3행과 4행에서 매크로 이름 `ADD` 와 `MUL` 을 정의한다. 매크로 상수를 정의하지 않았다고 해서 에러가 나는 것은 아니다. `ADD` 와 `MUL` 이 정의 되어있으므로 다음과 같은 결과를 얻을 수 있다
>ADD결과 : 4.40000
>MUL결과 : 3.630000 

`#ifndef` 는 "if not defined" 라는 뜻으로 해당매크로가 선언되어있지 않을때 컴파일을 한다는 점에서 `#ifdef` 와 반대라고 볼 수 있다. 
<hr>
