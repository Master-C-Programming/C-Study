1112 study<br><br>

## UOSPC 2019(div2) 풀어보기
<hr>

[UOSPC 2019 div2 문제 보기](https://github.com/all1m-algorithm-study/uospc/tree/master/2019)

<hr>

#### 승현이를 도와줘
```cpp
#include <iostream>
using namespace std;

int main()
{
	int B = 0;
	int N = 0;
	int C = 0;
	int required = 0;
	cin >> B;
	cin >> N;
	for (int i = 0; i < N; i++)
	{
		cin >> C;
		required = required + C;
	}
	if (B - required>=40) 
		cout << "possible" << endl;
	else
		cout << "impossible" << endl;
}
```

#### 메자이 풀스택

```cpp
#include <iostream>
using namespace std;

int main()
{
	int k1, d1, a1 = 0;
	int k2, d2, a2 = 0;
	int k, d, a = 0;
	cin >> k1 >> d1 >> a1;
	cin >> k2 >> d2 >> a2;
	k = k2 - k1;
	d = d2 - d1;
	a = a2 - a1;
	if (k * 4 + a * 2 >= 25)
		cout << "YES";
	else
		cout << "NO";

}
```
#### UOS Coder (div2)

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main()
{
	int N = 0;
	int cnt = 0;
	int result_cnt = 0;
	int pointor = 0;
	cin >> N;
	int* P = new int[N];
	for (int i = 0; i < N; i++)
	{
		cin >> P[i];
	}
	sort(P, P+N);

	for (int i = 0; i < N-1; i=pointor)
	{
		for (int j = i; j < N; j++)
		{
			pointor = j;
			if (P[i] == P[j])
				cnt++;
			else
				break;
		}
		if (result_cnt < cnt)
			result_cnt = cnt;
		cnt = 0;
	}
	result_cnt = result_cnt * 10;
	cout << result_cnt;
	
}
```
#### 팰린드롬 게임 (div2)

```c
#include <iostream>
#include <algorithm>
using namespace std;

int is_palindrome(int* A, int number)
{
	int begin = 0;
	int end = number-1;
	if (number % 2 == 0)
	{
		while (begin < end)
		{
			if (A[begin++] != A[end--])
				return 0;
		}
	}
	else
	{
		while (begin != end)
		{
			if (A[begin++] != A[end--])
				return 0;
		}
	}
	return 1;

}
int point(int* P,int number)
{
	int mid = (number-1) / 2;
	int cnt=0;
	for (int i = 0; i < mid ; i++)
	{
		if (P[i] < P[i + 1])
			cnt++;
	}
	if (cnt == mid)
		return 1;
	cnt = 0;
	for (int i = 0; i < mid; i++)
	{
		if (P[i] > P[i + 1])
			cnt++;
	}
	if (cnt == mid)
		return 2;
	else
		return 3;

}

int main()
{
	int N=0;
	cin >> N;
	int* A = new int[N];
	for (int i = 0; i < N; i++)
	{
		cin >> A[i];
	}
	if (!is_palindrome(A, N))
		cout << "D";
	else
		cout << point(A, N);


}
```

#### 무빙워크

```cpp
```

#### 근손실 싫어! 단백질 좋아!

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

char s[100000];
const char start[4] = "TAC";
int number_protein(char* string,int num)
{
	if (strncmp(start, string + num, 3)==0)
		return (strlen(string) - 3 - num) / 3;
	else
		return number_protein(string, num + 3);

}
int main()
{	
	cin >> s;
	
	int total=number_protein(s, 0);
	cout << total;
	
}
```

#### 미래관 엘리베이터

```cpp
```

#### 조별과제(small)

```cpp
```
<hr>