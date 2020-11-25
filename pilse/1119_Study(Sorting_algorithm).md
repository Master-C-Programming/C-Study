1119 study<br><br>


### 병합 정렬

병합 정렬은 대표적인 분할 정복 방법을 사용한 알고리즘 이다. 결과부터 말하자면 시간복잡도는 퀵정렬과 같은 `O(N log(N))`이다. 병합 정렬의 개념은 퀵정렬보다 쉬워 이해하기 어렵지 않다.
<br>

병합 정렬은 이전에 공부했던 분할 정복의 아이디어 "하나의 큰 문제를 두개의 작은 문제로 분할한 뒤에 각자 계산하고 나중에 합치는 방법"을 채택한다.

```c
#include <stdio.h>
int number = 8;
int size;
int sorted[8];
int count=0;

void merge(int a[],int m,int middle, int n)
{
	int i=m;
	int k=m;
	int j=middle+1;

	while(i<=middle && j<=n)
	{
		if(a[i]<=a[j])
		{
			sorted[k]=a[i];
			i++;
		}
		else
		{
			sorted[k]=a[j];
			j++;

		}
		k++

	}
	if(i>middle)
	{
		for(int t=j;t<=n;t++)
		{
			sorted[k]=a[t];
			k++;
		}
	}
		else
		{
			for(int t=i;t<=middle;t++)
			{
				sorted[k]=a[t];
				k++;
			}
		}
		for(int t=m;t<=n;t++)
		{
			a[t]=sorted[t];
		}
}

void mergesort(int a[],int m,int n)
{
	if(m<n)
	{
		int middle=(m+n)/2;
		mergesort(a,m,middle);
		mergesort(a,m,middle,n);
		merge(a,m,middlem,n);

	}
}

int main()
{
	int array[number]={7,6,5,8,3,5,9,1};
	mergesort(array,0,number-1);
	for(int i=0;i<number;i++)
	{
		printf("%d",array[i]);
	}
}
```

<hr>

### 힙 정렬

힙 정렬은 병합정렬과 퀵정렬만큼 빠른 알고리즘이다. 시간복잡도는 `O(N log(N))` 을 가진다. 힙정렬은 트리구조를 이용하여 정렬한다. 힙은 완전 이진 트리를 기반으로 하는 트리로 최솟값이나 최대값을 빠르게 구하기 위해 사용된다. 
<br>

힙에는 최소힙과 최대힙이 있는데 최소힙은 부모노드가 자식노드보다 항상 작은 트리를, 최대 힙은 부모노드가 자식노드보다 항상 큰 트리를 말한다.

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct treenode
{
    int key;
    struct treenode* left;
    struct treenode* right;

}treenode;


treenode* new_node(int key)
{
    treenode* node = malloc(sizeof(treenode));
    node->key = key;
    node->left = NULL;
    node->right = NULL;
    return node;
}
treenode* insert_node(treenode* root, int key)
{
    treenode* temp = root;
    if (root == NULL)
    {
        return new_node(key);
    }
    if (key < root->key)
        root->left= insert_node(root->left, key);
    else if (key > root->key)
        root->right= insert_node(root->right, key);
    return root;

	int main()
{
    treenode* root = NULL;

    root = insert_node(root, 30);
    root = insert_node(root, 20);
    root = insert_node(root, 10);
    root = insert_node(root, 40);
    root = insert_node(root, 50);
    root = insert_node(root, 60);
 
    return 0;

}
}

```

<hr>



