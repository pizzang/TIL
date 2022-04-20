## Array 배열

하나의 공간에 여러 개의 값을 담을 수 있음

단, **같은 자료형의 값들** 이어야 함

=> 배열의 각 인덱스 자리에 실제 값이 담김. 인덱스는 "0"부터 시작한다. 

#### 1. 배열 선언

- 자료형 배열식별자[];		`int arr1[];`

- 자료형[] 배열식별자;		`int[] arr2;`

#### 2. 배열 할당

이 배열에 몇개의 값이 들어갈지 배열의 크기를 정해주는 과정

지정한 갯수만큼 값이 들어갈 공간이 만들어짐

```java
int[] arr1; 
arr1 = new int[15];
		
int[] arr2 = new int[15];
```

#### 3. 배열의 각 인덱스에 값 대입

```Java
for(int i=0; i<arr1.length; i++){
	System.out.println(arr1[i]);
}
```

#### 4. 얕은 복사, 깊은 복사

- **얕은 복사** : 배열의 주소값만을 복사

- **깊은 복사** : 동일한 새로운 배열을 하나 생성해서 실제 내부값까지 복사

**해시코드** :  주소값을 십진수의 형태로 나타낸 것

해시코드가 동일하다고 해서 두개가 완전히 같을 순 없지만 
해시코드가 다르면 두개는 완전히 다른 거임

- #### 얕은복사

해시코드 같다.

```java
int[] origin = {1,2,3,4,5};
int[] copy = origin;
```

- #### 깊은복사

###### 1. copy[]에 origin[] 값을 각각 대입

```java
int[] origin = {1,2,3,4,5};
int[] copy = new int[origin.length];

for(int i=0; i<copy.length; i++){
    copy[i] = origin[i];
}
```

###### 2. arraycopy() : 몇 번 인덱스부터 몇 개를 어느 위치부터 넣을건지 직접 지정 가능

System.arraycopy(원본배열이름, 원본배열에서 복사를 시작할 인덱스, 복사본배열이름, 복사본배열에서 복사가 시작될 인덱스, 복사할 갯수)

```java
int[] origin = {1,2,3,4,5};
int[] copy = new int[10];

System.arraycopy(origin, 0, copy, 0, 5);
System.arraycopy(origin, 0, copy, 3, 5);

for(int i=0; i<copy.length; i++){
    System.out.print(copy[i] + " ");
}
```

###### 3. copyOf() : Arrays 클래스에서 제공. 원본 배열보다 큰 값을 제시하면 복사본 배열에 공간 생성. 0번 인덱스부터 내가 지정한 갯수 만큼 복사 진행

복사본배열 = Arrays.copyOf(원본배열이름, 복사할 갯수);

```java
int[] origin = {1,2,3,4,5};
int[] copy = Arrays.copyOf(origin, 10);

for(int i=0; i<copy.length; i++){
    System.out.print(copy[i] + " ");
}
```

######  4. clone() : 인덱스 직접 지정 X. 복사할 갯수 지정X. 원본배열과 완전히 똑같이.

복사본배열이름 = 원본배열이름.clone();

```java
int[] origin = {1,2,3,4,5};
int[] copy = origin.clone();

System.out.println(Arrays.toString(copy));
```



#### 배열의 아쉬운 점

한 번 지정한 배열의 크기는 변경 불가
어쩔 수 없이 다시 만들어야 함



#### 연결이 끊어진 기존의 배열은?

Heap영역에 둥둥 떠다니다가 일정시간이 지나면 가비지컬렉터가 삭제함
: 자동 메모리 관리
