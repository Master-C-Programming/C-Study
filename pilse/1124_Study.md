1124 study<br><br>


## UOSPC 2019 못푼 문제 다시 풀어보기

자료구조 수업시간에 그래프를 배우면서 저번 시간에 풀지못했던 문제들을 다시 한번 도전해 봤다.

#### 무빙워크

```cpp
#include <iostream>
#include <vector>
using namespace std;

int dfs_result;
vector<int> building[10001];
int visited[10001];
int dis[10001][10001];

void dfs(int v,int d)
{
	visited[v] = 1;
	for (int i = 0; i < building[v].size(); i++)
	{
		if (!visited[building[v][i]])
		{
			dfs(building[v][i], d + dis[v][building[v][i]]);
		}
		if (dfs_result < d)
			dfs_result = d;
	}

}

int main()
{
	int N;
	int result = 0;
	cin >> N;
	for (int i = 0; i < N-1; i++)
	{
		int temp1, temp2, temp_dis;
		cin >> temp1 >> temp2 >> temp_dis;
		building[temp1].push_back(temp2);
		building[temp2].push_back(temp1);
		dis[temp1][temp2] = temp_dis;
		dis[temp2][temp1] = temp_dis;

	}
	for (int i = 1; i <= N; i++)
	{
		dfs(i,0);
		if (result < dfs_result)
			result = dfs_result;
		dfs_result = 0;
		memset(visited, 0, 10001);
	}
	cout << result;

}
```

#### review

수업시간에 배운 dfs를 이용하여 문제를 풀었지만 solution을 보니 좀더 쉽게 풀 수있는 문제라는 것을 알게 되었다. `vector<pair<int,int>>` 로 `vector` 을 선언했다면 `dis[10001][10001]` 같은 메모리 낭비는 하지 않았을 것이다.
