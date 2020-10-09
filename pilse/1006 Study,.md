1006 study<br><br>

## c언어에서 Quick Sort 사용하기
<hr>

### Quick Sort란?
<br>

**`quicksort`** 란 `pivot`을 정하고 `pivot`보다 작은값들을 `pivot`의 왼쪽 `pivot`보다 큰 값들은 `pivot`의 오른쪽으로 위치시킨후 왼쪽값과 오른쪽값을 다시 재귀적으로 분할정복한다. <br>
* `O(nlogn)`의 성능을 보이는 정렬 알고리즘으로 최악의 경우에는 `O(n^2)`의 성능이지만 일반적으로는 빠른 성능을 나타내기에 주로 쓰이는 정렬방식이다. <br>

<hr>

### Quick Sort 의 순서
<br>

> 5(i) - 3 - 7 - 6 - 2 - 1(j) - 4(pivot)<br>
> 1(i) - 3 - 7 - 6 - 2 - 5(j) - 4(pivot) <br>
> 1 - 3(i) - 7 - 6 - 2(j) - 5 - 4(pivot)<br>
> 1 - 3(i) - 7 - 6 - 2(j) - 5 - 4(pivot)<br>
> 1 - 3 - 7(i) - 6 - 2(j) - 5 - 4(pivot)<br>
> 1 - 3 - 2(i) - 6 - 7(j) - 5 - 4(pivot)<br>
> 1 - 3 - 2 - 4(pivot) - 7 - 5 - 6 <br>
...<br>
> 1 - 2 - 3 - 4 - 5 - 6 - 7 - 8 - 9 - 10<br>

퀵정렬은 임의의 pivot 값을 기준으로 pivot 의 좌측에는 pivot 보다 작은값을 두고 우측에는 pivot 보다 큰 값을 두고자 한다.
이 행위는 pivot을 기준으로 좌 우로 이분화 된 리스트를 재귀적으로 반복했을 때 결국 정렬이 완성 된다는 방법 론이다.
보다 쉽게 설명하면 pivot보다 큰 값을 pivot index 보다 왼쪽에서 찾고 ( 큰 값 이 나타날 때까지 i index 를 증가시키도록 한다.)
pivot 보다 작은 값을 pivot index 보다 오른쪽에서 찾는다 ( 작은 값이 나타날 때까지 j index를 감소시키도록 한다. )
pivot을 기준으로 값 비교가 완료되었다면 index 결과 i , j 를 비교 해본다.
i 값이 j 값 보다 작거나 같다면 분명 pivot 을 기준으로 교환을 해야할 값이 있다는 뜻이 된다.
교환한 뒤 i 인덱스는 증가 j 인덱스는 감소 연산을 수행한다.
i 인덱스가 j 인덱스보다 작거나 같다면 계속 반복해서 수행한다.


<hr>

### c언어로 Quick Sort 구현하기 


```c
#include<stdio.h>


void quicksort(int* data, int start, int end)
{
	if(start >= end)
	return;

	int key =start;
	int i = start +1, j= end, temp;

	while(i<=j)
	{
		int key=start;
		int i=start+1, j=end , temp;

		while(i<=end&&data[i]<=data[key]>)
		i++;
		while(j>start&&data[j]>=data[key])
		j--;
		if(i>j)
		{
		temp=data[j];
		data[j]=data[key];
		data[key]=temp;
		}
		else
		{
		temp=data[i];
		data[i]=data[j];
		data[j]=temp;
		}
	}
	quickSort(data,start,j=1);
	quickSort(data,j+1,end);
}

```

<hr>

### `qsort()`로 구현하기 

C의 `stdlib.h` 에서는 `QuickSort`함수인 `qsort()`를 제공한다.
```c
void qsort(void *base, size _t nel, size_t width, int(*compare)(const void *,const *));
```
다음과 같이 사용할 수 있다.
```c
int static compare(const void*first, const void* second)
return(*(int*)first>*(int*)second);

int main ()
{
	int arr[]={1,4,2,5,6,87,9,};
	qsort(array,sizeof(array)/sizeof(int),sizeof(int),compare);
}
```

<hr>