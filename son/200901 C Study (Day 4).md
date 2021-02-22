20-09-01 C Study (Day 4)
=====
교제 : 윤성우의 열혈 C 프로그래밍  

chapter 1 ~ 3
<hr>

### C언어는 프로그래밍 언어이다.

한국인과 미국인이 의사소통을 하려면 어떤 것이 필요 할까?  
각각 한국어와 영어만 사용 가능하다면 한국어와 영어에 능통한 통역가가 필요 할 것이다.  
  
컴퓨터는 기본적으로 기계어로 작동하고 우리는 이 컴퓨터와 소통을 하기위해 통역가인 '컴파일러'에게 프로그래밍 언어로 의사를 컴퓨터에게 전달한다.

- __프로그래밍 언어란?__  
사람과 컴파일러가 이해할 수 있는 약속된 형태의 언어  
C언어 또한 프로그래밍 언어 중 하나이다.  
- __컴파일러의 역할?__  
프로그래밍 언어로 작성한 프로그램을 컴퓨터가 이해할 수 있도록 기계어로 변역하는 역할  
이러한 일을 '컴파일'이라 칭한다.

### C언어의 장점
1. __절차지향적__  
절차지향이란 '정해진 순서의 실행흐름'을 말한다.  
위에서 아래로 순서대로 프로그램이 진행하기에 이해하기에 큰 어려움이 없다.
2. __이식성이 좋음__  
CPU의 종류에 상관없이 실행 가능하며 운영체제의 차이에도 덜 민감하다.  
3.__좋은 프로그램의 성능__  
C언어는 사용하는 메모리의 양이 상대적으로 적고, 속도를 저하시키는 요소들을 최소화 하여 프로그램의 성능이 상대적으로 좋다.
<hr>

## 변수와 연산자

### 변수란?
값을 자장 할 수 있는 메모리 공간에 붙은 이름, 혹은 메모리 공간 그 자체.  

#### 변수 선언 및 초기화 방법

``` c
int main(void){
	int num; // 변수의 선언
	int num1 = 8; // 변수의 선언 및 초기화
	num = 7; // 변수의 초기화
	. . . .
}
```

#### 변수선언 시 주의할 사항
- 중괄호 내에 변수 선언시, 선언문은 중괄호 앞부분에 위치 할 것.
- 변수의 이름은 알파벳, 숫자, 언더바( _ )로 구성된다.
- C언어는 대소문자를 구분한다.
- 변수의 이름은 숫자로 시작할 수 없으며, 키워드도 변수의 이름으로 사용 불가능하다.
- 이름 사이에 공백이 삽입될 수 없다. ( 언더바를 활용하자 )

#### 변수의 자료형
- 정수형 변수 : 정수의 저장이 목적
- 실수형 변수 : 소수점 이하의 값을 지니는 실수의 저장이 목적

#### 다양한 연산자
C언어에는 많은 연산자들이 있다. 자세한 사항은 링크로 남긴다.  
[C언어 연산자](https://ko.wikipedia.org/wiki/C%EC%99%80_C%2B%2B%EC%9D%98_%EC%97%B0%EC%82%B0%EC%9E%90)