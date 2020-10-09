1008 study<br><br>

## Dynamic Programming(동적 계획법)
<hr>

### Dynamic Programming 이란?
<br>

* **`Dynamic Programming`** 이란 하나의 문제는 한번만 풀도록 하는 알고리즘이다. 이전에 계산한 결과는 배열에 저장해놓고 나중에 동일한 계산을 할 때 저장된 값을 반환함으로써 시간복잡도를 줄일 수있다.
<br>

* **`Dynamic Programming`** 은 큰문제를 작은문제로 나누고 작은문제에서 구한 정답이 큰문제에서도 동일할 때 사용할 수있다.
<br>

* **`Memoization`** 은 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거하여 프로그램 실행 속도를 빠르게 하는 기술이다.

<hr>

### Dynamic Programming이 필요할 때
<br>

일반적으로의 분할정복 기법은 같은 문제를 여러번 푼다는 단점을 가지고있다. 이를 극단적으로 보여주는 예시로 피보나치 수열이 있다. 피보나치 수열은 이전 두개의 값의 합으로 새로운 값을 만들어내는 수열로 다음과 같이 쓸 수있다.<br>
>fibo(i)=fibo(i-1)+fibo(i-2)

<br>

피보나치 함수를 **`Dynamic Programming`** 을 사용하지 않고 구현한것과 사용한것의 차이를 알아보자
```c
//dynamic programming 사용x
#include <stdio.h>
int fibo(n)
{
	if(n==1) return 1;
	if(n==2) return 1;
	return fibo(n-1)+fibo(n-2);
}
int main()
{
	printf("%d",d(50));
}
```
```c
//dynamic programming 사용
#include <stdio.h>
int dp[100];
int fibo(n)
{
	if(n==1) return 1;
	if(n==2) return 1;
	if(dp[n]!=0) return(dp[n]);
	return dp[n]=fibo(n-1)+fibo(n-2);
}
```

두 코드는 작은 수를 넣었을 때는 성능상 큰 차이를 보이지 않지만 숫자가 커질수록 엄청난 차이가 발생한다. 50을 두 코드에 넣는다고 생각해보면 **`Dynamic Programming`** 을 사용하지 않은 코드의 경우 `2^50`번의 계산을 하느라 프로그램이 값을 출력하지 못하지만 **`Dynamic Programming`** 을 사용한 코드는 `50`번의 계산만 필요하기때문에 값을 바로 출력할 수있다.
<hr>

### Dynamic Programming 문제 풀어보기

* __문제__<br>

>`7`
>`3` `8`
>`8` `1` `0`
>`2` `7` `4` `4`
>`4` `5` `2` `6` `5`

위 그림은 크기가 5인 정수 삼각형의 한 모습이다.

맨 위층 7부터 시작해서 아래에 있는 수 중 하나를 선택하여 아래층으로 내려올 때, 이제까지 선택된 수의 합이 최대가 되는 경로를 구하는 프로그램을 작성하라. 아래층에 있는 수는 현재 층에서 선택된 수의 대각선 왼쪽 또는 대각선 오른쪽에 있는 것 중에서만 선택할 수 있다.

삼각형의 크기는 1 이상 500 이하이다. 삼각형을 이루고 있는 각 수는 모두 정수이며, 범위는 0 이상 9999 이하이다.

* __입력__<br>
 첫째 줄에 삼각형의 크기 n(1 ≤ n ≤ 500)이 주어지고, 둘째 줄부터 n+1번째 줄까지 정수 삼각형이 주어진다.

* __출력__<br>
첫째 줄에 합이 최대가 되는 경로에 있는 수의 합을 출력한다.

```c
#include<stdio.h>
#include<stdlib.h>

int main()
{
    int N = 0;
    int result = 0;
    scanf("%d", &N);
    int **tri = malloc(sizeof(int *) * (N + 1));
    int **dp = malloc(sizeof(int *) * (N + 1));
    
     for (int i = 0; i < N + 1; i++)
    {
        tri[i] = malloc(sizeof(int) * (N + 1));
        dp[i] = malloc(sizeof(int) * (N + 1));
    }
    for (int i = 0; i < N; i++)
    {
        for (int j = 0; j <= i; j++)
        {
            scanf("%d", &tri[i][j]);
            dp[i][j] = 0;

        }
    }

    dp[0][0] = tri[0][0];
    for (int i = 1; i < N; i++)
    {
        for (int j = 0; j <= i; j++)
        {
            if (j == 0) {
                dp[i][j] = dp[i - 1][j] + tri[i][j];
            }
            else if (j == i) {
                dp[i][j] = dp[i - 1][j - 1] + tri[i][j];
            }
            else {
                if ((dp[i - 1][j - 1] + tri[i][j]) > (dp[i - 1][j] + tri[i][j]))
                    dp[i][j] = dp[i - 1][j - 1] + tri[i][j];
                else
                    dp[i][j] = dp[i - 1][j] + tri[i][j];
            }
        }
    }
    for (int i = 0; i < N; i++)
    {
        if (dp[N - 1][i] > result)
            result = dp[N - 1][i];
    }
    printf("%d", result);

    for (int i = 0; i < N + 1; i++)
    {
        free(tri[i]);
        free(dp[i]);
    }
    free(tri);
    free(dp);
    return 0;
}
```
* __풀이__<br>

`dp[i][j]`는 `tri[i][j]`의 삼각형이 `top-down`방식으로 내려오면서 `(i,j)` 까지의 합을 저장한다.
예를 들어 `tri`삼각형이 7-3-8을 지나왔다면 `dp`에는 18이 저장된다. 삼각형을 다 내려온 후 `dp[N-1]`중 가장 큰 값을 출력한다.<br>

**`Memoization`** 을 사용했기 때문에 같은 계산이 반복되는 일이 없어 시간복잡도를 낮출수 있다.
<hr>