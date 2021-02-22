1126 study<br><br>


## 다익스트라 알고리즘(Dijkstra algorithm)
**`Dijkstra algolithm`** 은 다이나믹 프로그래밍을 활용한 최단경로 탐색 알고리즘 이다. <br>
**`Dijkstra algolithm`** 의 특징은 특정한 하나의 정점에서 다른 모든 정점으로 가는 최단 경로를 알려준다는 것이다. 이를 위해 한 정점에서 인접한 다른 정점으로의 최단 경로를 저장하는 배열이 필요하고 이를 정점을 이동할 때마다 최단 경로로 바꿔줘야 한다.
```c
#include <stdio.h>
#define INF 100000

int a[6][6] =
{
	{0,2,5,1,INF,INF},
	{2,0,3,2,INF,INF},
	{5,3,0,3,1,5},
	{1,2,3,0,1,INF},
	{INF,INF,1,1,0,2},
	{INF,INF,5,INF,2,0},
};

int distance[6];
int visited[6];

int min_adj()
{
	int min = INF;
	int index = 0;
	for (int i = 0; i < 6; i++)
	{
		if ((!visited[i]) && (distance[i] < min))
		{
			min = distance[i];
			index = i;
		}
	}
	return index;


}

void dijkstra(int start)
{
	visited[start] = 1;
	for (int i = 0; i < 6; i++)
	{
		distance[i] = a[start][i];
	}
	int current = min_adj();
	for (int i = 0; i < 4; i++)
	{
		visited[current] = 1;
		for (int j = 0; j < 6; j++)
		{
			if ((!visited[j]) && (distance[j] > (distance[current] + a[current][j])))
				distance[j] = distance[current] + a[current][j];
		}
		current = min_adj();
	}

}

int main()
{
	dijkstra(0);
	for (int i = 0; i < 6; i++)
	{
		printf("%d ", distance[i]);
	}

}

```

### review

처음에 프로그램을 짤 때는
```c
if ((!visited[j]) && (distance[j] > (distance[current] + a[current][j])))
				distance[j] = distance[current] + a[current][j];
```
이부분을
```c
if ((!visited[j]) && (distance[j] > (a[start][current] + a[current][j])))
				distance[j] = a[start][current] + a[current][j];
```
이런식으로 해서 값이 잘 나오지 않았다. 아직까지 다이나믹 프로그래밍을 쓰는데 개념이 잘 잡히지 않은 것 같다. 다이나믹 프로그래밍 관련 문제들을 풀어보면서 익숙해질 필요가 있다.
<hr>
