0831 Study
------

### scanf함수에 대한 이해

* 정수형 입력 : scanf("%d", &n1); -> 입력받은 정수 값을 저장할 병수 이름 앞에 &
* &에 대한 이해 : 해당 변수의 주소값을 얻게됨
  
* 실수형(double) 입력 : %lf

cf) scanf_s 함수  -> #pragma warning(disable:4996)

### if와 else

* if문의 코드 구성 
```c
if(n>5) 
    printf("5보다 크다.");
```
<- 중괄호 사용도 가능
* if~else문의 중첩
```c
if(num<0) {
    printf("음수입니다.\n");
}
else {
    if(num==0)
        printf("0입니다.\n");
    else
        printf("양수입니다.\n");
}
```
----위의 코드를 간단하게 나타내자면
```c
if(num<0)
    printf("음수입니다.\n");
else if(num==0)
    printf("0입니다.\n");
else
    printf("양수입니다.\n");
```
* 필요에 따라 else if 여러번 추가 가능
* 조건 연산자의 활용
  - 구성 : '조건' ? A : B;
  - 의미 : '조건'이 참이면 A, '조건'이 거짓이면 B
  - ex) x=(y>0) ? 10 : 20;
  
### switch문

* 기본적인 구조
```c
switch(n)
{
    case 1:
        printf("A");
    case 2:
        printf("B");
    case 3:
        printf("C");
    default:
        printf("default");
}
```
* 일반적인 사용모델 : switch문 + break문 = switch문을 그냥 빠져나감!

* 한계점 : 비교 연산 불가능

* 한줄에 두개이상의 레이블을 둘수 있음 ex) case 2 : case 3 : case 5 :\

### goto구문

* 알고는 있으나 사용 안하는 습관 들이기
  
* goto구문 이해 : 프로그램의 실행을 특정 위치로 이동시키는 기능을 제공
  
* goto rabbit; -> 레이블 rabbi으로 가서, 실행을 이어가라

* goto문은 자신이 속해있는 함수 내에서만 레이블을 찾음
  
### scope에 대한 이해

* 지역변수(local variable) : 선언된 지역을 벗어나면 메모리 공간에서 소멸
```c
if num = 1;

if(num==1)
{ // 별도의 지역 A
    int num = 2;
    num++;
    printf("%d", num);
}
else
{ // 별도의 지역 B
    num++;
    printf("%d", num);
}
```