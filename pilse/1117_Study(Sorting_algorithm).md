1117 study<br><br>

## 정렬 알고리즘

<hr>

이전에 `quick sort` 를 공부한 적이 있다. 오늘은 `quick sort`뿐만 아니라 다른 정렬 알고리즘에 대해서도 알아볼것이다.<br>
정렬 알고리즘에는 `선택정렬(selection sort)` `버블정렬(bubble sort)` `삽입정렬 (insert sort)` `퀵 정렬(quick sort)` `병합정렬 (merge sort)` `힙정렬 (heap sort)` 등 이있고 상황에 따라 유리한 정렬방식이 다르다.


<hr>

### 선택 정렬

선택 정렬은 매 사이클마다 가장 작은 것을 선택해서 제일 앞으로 보내는 알고리즘이다.

```c
#include <stdio.h>

int main()
{
	int i,j,min,index,temp;
	int array[10]={{2,1,6,4,5,3,7,10,9,8};
	min=10000;
	for(i=0;i<10;i++)
	{
		for(j=i;j<10;j++)
		{
			if(min>array[j])
			{
				min=array[j];
				index=j;
			}
			temp=index[j];
			array[i]=array[index];
			array[index]=temp;
		}
	}

}
```
선택정렬은 N개의 데이터가 있을 때 N*(N+1)/2 의 계산을 수행하므로 `O(N^2)`의 시간 복잡도를 가진다.

<hr>

### 버블 정렬

버블정렬은 가까이에 있는 두 숫자를 비교해서 더 작은 숫자를 앞으로 보내주는 것을 반복하는 알고리즘이다.

```c
#include <stdio.h>

int main()
{
	int i,j,temp;
	int array[10]={2,1,6,4,5,3,7,10,9,8};
	for(int i=0;i<10;i++)
	{
		for(int j=0;j<9-i;j++)
		{
			if(array[j]>array[j+1])
			{
				temp=array[j];
				array[i]=array[j+1];
				array[j+1]=temp;
			}
		}
	}
}
```
시간복잡도는 선택정렬과 같은 `O(N^2)` 이지만 컴퓨터 내부적인 연산이 가장 비효율적으로 일어나기 때문에 가장 좋지않은 알고리즘이다.

<hr>

### 삽입 정렬

삽입정렬은 각 숫자를 적절한 위치에 삽입하는 방법으로 문제를 해결한다. 앞의 두가지 방법의 정렬과 다르게 삽입정렬은 필요 할 때만 위치를 바꾼다.

```c
#include <stdio.h>

int main()
{
	int i,j,temp;
	int array[10]={2,1,6,4,5,3,7,10,9,8};
	for(i=0;i<10;i++)
	{
		j=i;
		while(j>=0&&array[j]>array[j+1])
		{
			temp=array[j];
			array[j]=array[j+1];
			array[j+1]=temp;
			j--;
		}
	}

}
```
삽입정렬의 시간복잡도는 `O(N^2)` 로 앞선 두 알고리즘과 비슷해 보이지만 삽입정렬은 데이터들이 일단 정렬이 되어있다고 가정하는 알고리즘이기 때문에 데이터들이 거의 정렬이 마쳐진 상태에서는 상당히 빠르다는 특징을 가진다.

<hr>

###