0922 study<br><br>

## 콘솔 입출력과 파일 입출력2
<hr>

### `fgets()` 와 `fputs()`
<br>

| 함수의 원형 | 설명 |
|-------------|-----|
|char* fgets(char* s,int n,FILES* stream);|키보드/파일 로부터 문자열을 입력받음 <br>파일 끝 도달:NULL포인터 반환|
|int fputs(const char* s, FILE* stream);|모니터/파일 에 문자열을 출력<br>실패: EOF반환|

**`fgets()`** 함수는 문자열 입력함수로 `gets()` 함수와 같은 기능을 하며 추가적으로파일 스트림을 지정하거나 표준 입력 스트림을 지정할 수있는 특징이 있다.
**`fputs()`** 함수는 문자열 출력 함수 `puts()` 함수와 같은 기능을 하며 추가적으로 파일 스트림을 지정하거나 표준 출력 스트림을 지정할 수 있는 특징이 있다.<br><br>
* 예제
```c
#inlcude<stdio.h>

int main ()
{
    FILE* stream;
    char buffer[50];

    stream = fopen ("data3.txt","w");
    if(stream==NULL)
    puts("파일 열기 오류");

    fgets(buffer,sizeof(buffer),stdin);
    fputs(buffer,stream);

    fclose(stream);

}
```
<hr>

### `fprintf()` 와 `fscanf()`
<br>

| 함수의 원형 | 설명 |
|-------------|-----|
|int fscanf(FILE* stream,const char* format, ...);|키보드/파일 로부터 자료형에 맞춰 데이터를 입력|
|int fprintf(FILE* stream,const char* format, ...);|모니터/파일 자료형에 맞춰 데이터를 출력|
`fprintf()` 함수와 `fscanf()`함수는 %c, %d, %s 등과 같은 형식을 파일에 입출력 할수 있다. 이들 함수의 특징은 파일에 데이터를 입출력 할 수있는 기능을 가지고 있다는 것이다.
<br><br>

* 예제
```c
#include<stdio.h>

 int main()
 {
     FILE* stream1;
     FILE* stream2;
     
     char name[10]="";
     int kor=0,eng=0,total=0;

     stream1=fopen("data4.txt","r");
     stream2=fopen("data5.txt","w");

     fscanf(steram1,"%s %d %d %d \n",name,&kor,&eng,&total);
     fprintf(steram1,"%s %d %d %d \n",name,kor,eng,total);

     fclose(stream1);
     fclose(stream2);

     return 0;

 }
```


<hr>

### `feof()`

|함수|파일의 끝에서 반환하는 값|
|----------|-----------------|
|`fgetc()`|EOF(-1)|
|`fgets()`|NULL(0)|
|`fscanf()`|EOF(-1)|
이와 같이 파일의 끝을 검사하는 방법이 함수마다 다르다. 이것들을 각각 다 기억하기는 어렵기 때문에 `feof()`함수를 사용한다. `feof()`는 파일에 끝에 도달한 경우 0이 아닌값을 반환한다.
<br><br>

* 예제
```c
#include <stdio.h>
int main()
{
    FILE* stream1;
    FILE* stream2;
    char buffer[50];

    stream1=fopen("data1.txt","r");
    stream2=fopen("data2.tst","w");

    while(!feof(stream1))
    {
        fgets(buffer,sizeof(buffer),stream1);
        fputs(buffer,stream);

        fclose(steram1);
        fclose(stream2);

        return 0l
    }
}
```
<hr>

