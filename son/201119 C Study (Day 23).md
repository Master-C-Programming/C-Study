20-11-19 C Study (Day 23)
=====
UOSPC 2019 문제 풀이

프로그래밍 경진대회 코딩연습

<hr>

## 승현이를 도와줘

작년에 이어서 올해도 UOSPC 서울시립대 알고리즘 경진대회가 개최되었다!  
승현이는 올해 특별하게 문제를 맞춘 사람에게 문제당 하나씩 풍선을 달아주려고 한다. 하지만
필요한 만큼의 헬륨 가스를 구입하는데 40만원의 비용이 들어간다고 한다. 월급쟁이 승현이를 도
와서 제한된 예산 내에서 헬륨 풍선을 준비할 수 있는지 알아내는 프로그램을 작성해보자. 

__입력__  

첫째 줄에 현재 남은 예산 금액 B가 주어진다. (1 <= B <= 2000)  
둘째 줄에 앞으로 지출될 목록의 수 N이 주어진다. (1 <= N <= 50)  
세번째 줄에 각 목록의 지출될 금액 Ci가 한 줄에 주어진다. (1 <= Ci <= 100)  

__출력__  

알고리즘 소모임 AL林이 예산이 40만원 이상 남아 풍선을 달아줄 수 있으면 possible, 달아줄 수
없으면 impossible을 출력한다.

## Code 1

```c
#include <stdio.h>

int main()
{
	int current_money =1;
	int n = 1;
	int c = 1;
	int sum = 0;
	
	printf("현재 남은 예산 금액: ");
	scanf_s("%d", &current_money);
	if (current_money < 1 || 2000 < current_money)
	{
		printf("잘못된 입력 \n");
		return 0;
	}
	printf("지출될 목록의 수: ");
	scanf_s("%d", &n);
	if (n < 1 || 50 < n)
	{
		printf("잘못된 입력 \n");
		return 0;
	}
	printf("지출될 금액 목록: ");
	for (int i = 0; i < n; i++) 
	{
		scanf("%d", &c);
		sum += c;
	}
	if ((current_money - sum) < 40)
		printf("impossible \n");
	else
		printf("possible \n");

	return 0;
}
```

## 메자이 풀스택
많은 사람들에게 사랑받는 L 게임에는 메자이의 영혼약탈자(이하 메자이) 라는 아이템이
있다. 이 아이템은 다음과 같은 효과를 가지고 있다.  
- 아이템 구입 시에 스택이 0 으로 활성화
- 플레이어가 Kill 했을 때, 스택이 +4 증가
- 플레이어가 Assist 했을 때, 스택이 +2 증가
- 플레이어가 Death 했을 때, 스택이 -10 감소
- 스택은 0 미만으로 내려가거나 25 를 초과하지 않음.  

이 게임에 푹 빠진 수정이는 문득 특정한 Kill/Death/Assist 기록으로 메자이의 스택을
25 로 만들 수 있는지 궁금해졌다. Kill, Death, Assist 를 기록하는 사건이 독립이라고 할
때, 수정이를 도와 메자이의 스택을 최대로 만들 수 있는지 확인해봅시다.

__입력__  

메자이를 사기 전의 누적 Kill, Death, Assist 횟수(k~1~, d~1~, a~1~)와  
메자이를 산 후의 누적 Kill, Death, Assist 횟수(k~2~, d~2~, a~2~)가 공백으로 주어집니다.  
이때 k, d, a는 정수이며, 1 ≤ k, d, a ≤ 1000의 범위를 가집니다.  

__출력__  

메자이를 25 스택으로 만들 수 있으면 YES , 없으면 NO 를 출력합니다.

## Code 2

```c
#include <stdio.h>

int main()
{
	int bk, bd, ba;
	int ak, ad, aa;
	int mejai_stack = 0;
	
	printf("메자이 구입 전 Kill, Death, Assist: ");
	scanf_s("%d %d %d", &bk, &bd, &ba);

	printf("메자이 구입 후 Kill, Death, Assist: ");
	scanf_s("%d %d %d", &ak, &ad, &aa);
	if ( ( bk < 1 || 1000 < bk) ||
		 ( bd < 1 || 1000 < bd) ||
		 ( ba < 1 || 1000 < ba) ||
		 ( ak < 1 || 1000 < ak) ||
		 ( ad < 1 || 1000 < ad) ||
		 ( aa < 1 || 1000 < aa)   )
	{
		printf("잘못된 입력 \n");
		return 0;
	}

	mejai_stack = (4 * (ak - bk) + 2 * (aa - ba));

	if (mejai_stack < 25)
	{
		printf("NO \n");
	}
	else
		printf("YES \n");

	return 0;
}
```

## UOS Coder

온라인 저지 사이트 ‘UOS Coder’에서는 정기적으로 프로그래밍 대회를 연다. UOS Coder에는 자신
의 실력을 나타내는 지표인 레이팅이 있다. 매번 열리는 프로그래밍 대회에서 학생들은 경쟁하고
등수에 따라 레이팅이 올라가거나 내려간다.  
UOS Coder의 운영자 MK는 새로운 ‘포인트’ 시스템을 도입하려고 한다. 분기별로 유저는 목표 레
이팅을 설정하고 레이팅을 달성할 때마다 10 포인트를 얻을 수 있다. 즉, k번째 대회 후 레이팅을
Rk, 목표 레이팅을 Rg라 하면 다음 식이 성립할 때 대회가 끝나고 10 포인트를 얻는다.  

R~k-1~ < R~g~ ≤ R~k~

MK는 새로운 포인트 시스템을 도입하기 전에 지난 이용자가 얻을 수 있었던 최대 포인트를 계산
해보려고 한다. MK를 도와서 이용자가 얻을 수 있었던 최대 포인트를 계산하는 프로그램을 작성
해보자.  

__입력__  

첫째줄에 현재까지 개최된 대회의 횟수 N(1 ≤ N ≤ 100)이 주어진다. 두번째줄에는 최대 포인트
를 계산하려는 이용자의 레이팅을 나타내는 자연수가 주어진다. 이용자의 레이팅은 1000보다 작
거나 같다.

__출력__

첫째줄에 이용자가 받을 수 있었던 최대 포인트를 출력한다. <U>처음 이용자가 설정한 목표 레이팅
은 N번동안 변경할 수 없다고 가정한다.</U>  


## Code 3

```c
#include <stdio.h>

#define MAX_COMP_NUM 1000

int main()
{
	int N; 
	int rating[MAX_COMP_NUM];
	int max_rate = 1;
	int rating_point = 0;
	int max_point = 0;

	printf("개최된 대회의 횟수: ");
	scanf_s("%d", &N);

	if ( N < 1 || 1000 < N )
	{
		printf("잘못된 입력 \n");
		return 0;
	}

	printf("이용자의 레이팅: ");
	for (int i = 0; i < N; i++)
	{
		scanf_s("%d", rating+i);
		if (rating[i] < 1 || 1000 < rating[i])
		{
			printf("잘못된 입력 \n");
			return 0;
		}
		if (rating[i] > max_rate)
			max_rate = rating[i];
	}

	for (int goal_rate = 2; goal_rate <= max_rate; goal_rate++)
	{
		rating_point = 0;
		for (int k = 0; k < N - 1; k++)
		{
			if (rating[k]< goal_rate && goal_rate <= rating[k+1])
			{
				rating_point += 10;
			}
		}
		if (rating_point > max_point)
			max_point = rating_point;
	}

	printf("이용자의 최대 포인트: %d", max_point);

	return 0;
}
```

## 팰린드롬(palindrome) 게임

팰린드롬 수열이란 앞에서부터 읽을 때와 뒤에서부터 읽을 때 똑같은 수열을 말한다.  
{3}, {2, 2}, {3, 3, 3}, {1, 2, 2, 1}, {3, 2, 1, 2, 3}은 모두 팰린드롬 수열이다.  
팰린드롬 게임의 점수의 획득은 다음과 같다.  

1. 길이가 3이상이면서 중심으로 갈수록 증가하는 팰린드롬 수열 : 1점
2. 길이가 3이상이면서 중심으로 갈수록 감소하는 팰린드롬 수열 : 2점
3. 길이가 3미만이거나 1 또는 2가 아닌 수열 : 3점

예를 들어 {1}, {2, 2}, {3, 3, 3}, {2, 1, 3, 1, 2}는 모두 3점 팰린드롬 수열이다.  
주어진 수열로 팰린드롬 게임을 했을 때 얻을 수 있는 점수를 출력하는 프로그램을 작성하시오.  

__입력__

첫째줄에 수열 A의 길이 N이 주어진다. 수열의 길이는 5 이상이다. (5 ≤ N ≤ 1000)
둘째줄에 수열 A의 원소 A~i~가 주어진다.(1 ≤ A~i~ ≤ 1,000,000,000)

__출력__

첫째 줄에 수열 A로 팰린드롬 게임을 했을 때 얻을 수 있는 점수를 출력한다. 만약 팰린드롬 수
열이 아니라면 “D”를 출력한다.

## Code 4

```c
#include <stdio.h>

#define MIN_PALINDROME 5
#define MAX_PALINDROME 1000
#define ELEMENT_UPPER_LIMIT 1000000000

int main()
{
	int N; 
	int palindrome[MAX_PALINDROME];
	char is_palindrome = 'D';
	int palindrome_mid_pointer;
	int is_decreasing = 0;
	int is_increasing = 0;

	printf("수열 A의 길이: ");
	scanf_s("%d", &N);

	if ( N < MIN_PALINDROME || MAX_PALINDROME < N )
	{
		printf("잘못된 입력 \n");
		return 0;
	}

	printf("수열 A의 원소 입력: ");
	for (int i = 0; i < N; i++)
	{
		scanf_s("%d", palindrome +i);
		if (palindrome[i] < 1 || ELEMENT_UPPER_LIMIT < palindrome[i])
		{
			printf("잘못된 입력 \n");
			return 0;
		}
	}
	
	palindrome_mid_pointer = N / 2;

	for (int j = 0; j < palindrome_mid_pointer; j++)
	{
		if (palindrome[j] != palindrome[N - 1 - j])
		{
			printf("%c", is_palindrome);
			return 0;
		}
	}
	
	for (int k = 0; k < (palindrome_mid_pointer - 1); k++)
	{
		if (palindrome[k] < palindrome[k + 1])
			is_increasing = 1;
		if (palindrome[k] > palindrome[k + 1])
			is_decreasing = 1;
	}
	if (N % 2 == 1)
	{
		if (palindrome[palindrome_mid_pointer - 1] < palindrome[palindrome_mid_pointer])
			is_increasing = 1;
		if (palindrome[palindrome_mid_pointer - 1] > palindrome[palindrome_mid_pointer])
			is_decreasing = 1;
	}

	if (is_increasing == 1 && is_decreasing == 0)
		printf("1점");
	else if (is_increasing == 0 && is_decreasing == 1)
		printf("2점");
	else
		printf("3점");

	return 0;
}
```

## 후기

시험시간은 3시간  

코드 4가지를 작성하는 데 걸린 시간 : 1시간 20분  

뒤로 갈수록 어려워지는 걸 보아 아직 코딩 실력이 많이 부족한 것 같다.