20-11-24 C Study (Day 24)
=====
UOSPC 2019 문제 풀이

프로그래밍 경진대회 코딩연습

<hr>

## 근손실 싫어! 단백질 좋아!

DNA는 세 개의 염기로 묶어서 하나의 트리플렛 코드를 이룬다. 이로부터 mRNA가 각
염기에 대응하는 염기 서열을 만들어내는데, 이를 전사라고 하며, 이렇게 만들어진
mRNA의 세 개의 염기를 묶어 코돈이라고 한다.

mRNA의 코돈 상태에 따라 단백질을 구성하는 아미노산의 종류와 결합 순서가 결정되게
된다

어떤 코돈이 어떤 아미노산을 만들어내는지는 위의 표처럼 이미 밝혀져있다. 이때, `AUG`
코돈은 “개시 코돈”으로서, 모든 아미노산 합성이 시작되는 코돈이자 메싸이오닌 아미노
산을 만들어내는 코돈이다. 그리고 `UAA`, `UAG`, `UGA` 코돈은 “종결 코돈”으로, 아미노산을
합성하지 않고 아미노산의 생성을 중단한다.

위 과정을 요약하면 다음과 같다.
1. DNA 의 염기 서열이 주어진다  
	TAC AGA ACA AAA ATT
2. 위 DNA 로부터 상보적으로 전사된 mRNA 의 서열을 알아낸다.  
	AUG UCU UGU UUU UAA
3. 염기 서열에 해당하는 코돈을 해석한다.  
	메싸이오닌 - 세린 - 시스테인 - 페닐알라닌  

생명과학을 공부하는 노이만은 웰니스에서 벤치프레스를 하던 도중 문득 염기 서열에서
생성될 수 있는 아미노산의 수가 궁금해졌다. mRNA를 앞에서부터 해석할 수 있도록
DNA의 염기 서열이 주어질 때, 노이만을 도와 생성할 수 있는 단백질의 아미노산 개수
를 구해보자.

__입력__  

DNA의 트리플렛코드가 문자열 s로 주어진다. (1 ≤ length(s) ≤ 100,000)

__출력__  

전사된 mRNA에서 생성되는 아미노산의 개수를 출력한다.

## Code 1

```c
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX_DNA_LENGTH 100000
#define BUFFER_LENGTH 4

char* change_mRna(char* dna)
{
	char c = *dna;
	int i = 0;
	while (c != '\0')
	{
		switch (c)
		{
		case 'A' :
			*(dna + i) = 'U';
			break;
		case 'T' :
			*(dna + i) = 'A';
			break;
		case 'C' :
			*(dna + i) = 'G';
			break;
		case 'G' :
			*(dna + i) = 'C';
			break;
		}
		i++;
		c = *(dna + i);
	}
}
int is_initcodon (char* dna)
{
	if (!strcmp(dna, "AUG"))
		return 1;
	else
		return 0;
}

int is_closingcodon(char* dna)
{
	if (!strcmp(dna, "UAA"))
		return 1;
	else if (!strcmp(dna, "UAG"))
		return 1;
	else if (!strcmp(dna, "UGA"))
		return 1;
	else
		return 0;
}

int main()
{
	char s[MAX_DNA_LENGTH];
	char dna_buff[BUFFER_LENGTH];
	int i = 0;
	int start_copy = 0;
	int amino_acid_num = 0;

	printf("염기 서열 입력: ");
	fgets(s, MAX_DNA_LENGTH, stdin);
	change_mRna(s);
	do
	{
		strncpy(dna_buff, s + i, BUFFER_LENGTH - 1);
		dna_buff[BUFFER_LENGTH - 1] = '\0';

		if (start_copy) 
		{
			while (!is_closingcodon(dna_buff)) 
			{
				amino_acid_num++;
				i += 3;
				strncpy(dna_buff, s + i, BUFFER_LENGTH - 1);
				dna_buff[BUFFER_LENGTH - 1] = '\0';
			}
			break;
		}
		if (is_initcodon(dna_buff) && !start_copy)
		{
			start_copy = 1;
			amino_acid_num++;
		}
		i += 3;
	} while (*dna_buff != '\0');

	printf("아미노산의 개수: %d", amino_acid_num);

	return 0;
}
```

## 후기

이번 문제는 입력 받은 문자열을 얼마나 잘 다루는 가를 판단하는 문제 같다.  
문제를 푸는 과정에서 기억이 가물가물해 구글링을 많이 했었는데 확실히 내가 library를 잘 이용하지 못하고 많이 사용해보지 못한 것이 드러난 것 같다.  