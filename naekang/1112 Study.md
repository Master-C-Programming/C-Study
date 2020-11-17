# 1117 Study
------

### 'ptr ='과 '*ptr ='의 차이점
 * 'ptr =' 형태는 포인터 변수에 주소를 저장
  ```c
  short *ptr;
  ptr = (short *)0x0000006C; // 포인터 변수 ptr에 주소를 직접 대입
  ```

 * '*ptr =' 형태는 포인터가 가리키는 대상에 값을 저장
  ```c
  short *ptr;
  ptr = (short *)0x0000006C; /* ptr변수에 0x0000006C값을 대입 */
  *ptr = 0x0412; /* 0x0000006C 번지에 0x0412값을 대입함 */
  ```

### 다른 함수에 선언된 지역 변수 사용하기
 * 매개변수로 다른 함수의 변수 값 받기
  ```c
  #include <stdio.h>
  void Test(short data)
  {
      short soft = 0;
      soft = data;
  }

  void main()
  {
      short tips = 5;
      Test(tips); // data = tips
  }
  ```
 * 매개변수로 다른 함수의 변수 주소 받기
  ```c
  #include <stdio.h>
  void Test(short *ptr)
  {
      short soft = 0;
      soft = *ptr;
      *ptr = 3;
  }

  void main()
  {
      short tips = 5;
      Test(&tips);
  }
  ```
  -> Test함수에서 tips변수 이름은 사용할 수 없으나 tips 변수의 주소를 ptr포인터가 가지고 있기 때문에 *ptr을 사용하여 해당 주소에 저장된 값을 가져옴

  ### 두 변수의 값 서로 바꾸기
  * 임시로 보관하는 변수를 하나 더 추가해야함
  * 직접 주소 지정 방식으로 변수 값 교환하기
  ```c
  #include <stdio.h>

  void Swap(int a, int b)
  {
      int temp = a;
      a = b;
      b = temp;
  }

  void main()
  {
      int start = 96, end = 5;
      printf("before : start = %d, end = %d\n", start, end);
      if(start > end) {
          Swap(start, end);
      }
      printf("after : start = %d, end = %d\n", start, end);
  }
  ```
  -> 값이 바뀌지 않음(main함수의 start, end와 상관없이 변경된 변수가 a,b이기 때문)

  ### 포인터를 이용해 두 변수 값 바꾸기
  ```c
  #include <stdio.h>

  void Swap(int *pa, int *pb)
  {
      int temp = *pa;
      *pa = *pb;
      *pb = temp;
  }

  void main()
  {
      int start = 96, end = 5;

      printf("before : start = %d, end = %d\n", start, end);
      if(start > end) {
          Swap(&start, &end);
      }
      printf("after : start = %d, end = %d\n", start, end);
  }
  ```