0915 study<br><br>

### 동적할당
---
#### 동적할당의 필요성
* 고정된 메모리를 할당받을 때의 단점 <br>
    - 선언된 배열 요수 수가 사용된 요소 수보다 '많은 경우' 메모리의 낭비 발생<br>
    - 선언된 배열요소의 수가 사용된 요소의 수보다 '적은 경우' 메모리의 부족발생<br>
    - 배열 선언시 배열 길이에 변수를 설정한 경우 에러발생

---
#### 동적 메모리를 할당하는법
malloc()함수와 free()함수 사용
```c
#include<stdio.h>
void* malloc(size_t size); //동적 메모리 할당 함수
void free(void* p) //동적 메모리 헤제 함수
```

---
#### 동적할당을 이용한 문제
'kakao 2017 코딩테스트 1차-1번'<br>
```c
#include <stdio.h>

int main()
{
    int n = 0;
    scanf("%d", &n);
    int* arr1 = malloc(sizeof(int) * n);
    int* arr2 = malloc(sizeof(int) * n);
    int* arr3 = malloc(sizeof(int) * n);
    int* arr4 = malloc(sizeof(int) * n);

    for (int i = 0; i < n; i++)
    {
        scanf("%d", &arr1[i]);

    }

    for (int i = 0; i < n; i++)
    {
        scanf("%d", &arr2[i]);

    }
    for (int i = 0; i < n; i++)
    {
        arr3[i] = (arr1[i] | arr2[i]);

    }
    for (int x = 0; x < n; x++)
    {
        for (int i = n-1; i >= 0; i--)
        {
            if (i)
            {
                arr4[i] = arr3[x] % 2;
                arr3[x] = arr3[x] / 2;
            }
            if (!i)
                arr4[i] = arr3[x];

        }
        for (int i = 0; i < n; i++)
        {
            if (arr4[i])
                printf("#");
            if (!arr4[i])
                printf(" ");
        }
        printf("\n");

    }
    free(arr1);
    free(arr2);
    free(arr3);
    free(arr4);
    return 0;
}
```
---
#### 2차원 배열 동적할당

* 2차원 배열의 동적할당이 필요할 때<br>
     -  2중 포인터를 사용하여 할당해 준다.<br>

---
 #### 2차원 배열 동적 메모리를 할당하는법

```c
 #include<stdio.h>
 #include<stdlib.h>
 int main()
 {      //5*4배열이 필요하다고 가정
int** p = malloc(sizeof(int) * 5);
for (int i = 0; i < 5; i++)
	{
		p[i] = malloc(sizeof(int) * 4);
	}

	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 4; j++)
		{
			p[i][j] = i + j;
		}

	}

	for (int i = 0; i < 5; i++)
	{
		free(p[i]);
	}
	free(p);
 }
 ```

* 해제는 할당의 역순으로 해준다.