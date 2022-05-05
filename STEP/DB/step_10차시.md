10차시 : 프로그래밍 자료구조1 (List)

# Collection List 컬렉션 리스트

------

## 컬렉션(Collection)의 필요성

### 배열의 문제점을 개선하기 위해 제공

1. 한번 크기를 지정하면 변경할 수 없다
   - 기록시 배열공간의 크기가 부족하면 에러가 발생하기 때문에, 
     배열 공간 할당시 미리 넉넉한 크기로 할당을 하게 된다.(메모리 낭비)
   - 한번 할당된 배열공간은 필요에 따라 늘리거나 줄일 수 없다.
2. 배열에 기록된 데이터에 대한 중간 위치의 추가, 삭제가 불편하다.
   - 배열은 추가 / 삭제 알고리즘이 기본적으로 뒤에 추가, 뒤부터 삭제되는 구조임
   - 배열에 대해 중간 또는 앞에 추가 /  삭제시에는 기록된 데이터들을 하나씩 뒤로 밀어내거나, 앞으로 한칸씩 이동시키는 처리에 대한 복잡한 알고리즘이 필요하다.
3. 한 타입의 데이터만 저장 가능하다.



### Collection이란?

자바에서는 자료를 구조적으로 처리하는 방법인 자료구조(Data Structure)가 내장이 되어 있는 클래스들을 제공하고 있다. 
-배열의 단점이 보완된 기능들을 제공하고 있으며, 
-여러 종류의 **객체들을 저장**할 수 있고, 
-저장 용량에 제한이 없으며, 
-맨 앞 추가, 중간 위치 추가, 뒤에 추가, 맨 앞 및 중간 위치 삭제, 뒤 삭제, 정렬(Sort) 등의 
기능 처리가 메소드로 간단하게 사용할 수 있도록 제공이 되고 있다.
java.util 패키지에서 제공이 되고 있으며, **인터페이스**를 통해서 표준화된 사용방법을 제공하고 있다.



### 컬렉션의 장점

1. 저장하는 크기의 제약이 없다
2. 추가, 삭제, 정렬 등의 기능처리가 간단하게 해결된다.
   - 자료를 구조적으로 처리하는 자료구조가 내장되어 직접적인 알고리즘 구현이 필요없다.
3. 여러 타입의 객체를 저장할 수 있다.
   - **컬렉션은 객체만 저장하기 때문에**, 필요에 따라 기본 자료형(Primitive Type) 데이터를 저장해야 하는 경우 java.lang 패키지에서 제공되는 Wrapper클래스들을 사용하여 데이터를 박싱(Boxing)하여 객체로 변환한 다음 저장한다.



### 자료구조란?

데이터(자료)를 메모리에서 구조적으로 처리하는 방법론

![image-20220427125835942](C:\Users\김유미\AppData\Roaming\Typora\typora-user-images\image-20220427125835942.png)



### java.util 패키지의 컬렉션 관련 주요 인터페이스

![image-20220427125956542](C:\Users\김유미\AppData\Roaming\Typora\typora-user-images\image-20220427125956542.png)



### List 인터페이스

- 자료들을 배열처럼 **순차적으로 저장**하는 자료 구조
- **인덱스로 관리**되며, 객체의 **중복된 저장이 가능**
- 구현 클래스는 ArrayList 와 Vector, LinkedList가 있음

### List 계열 주요 메소드

![image-20220428192458399](C:\Users\김유미\AppData\Roaming\Typora\typora-user-images\image-20220428192458399.png)

### ArrayList

List의 후손으로, 초기 저자 용량은 10으로 자동 설정 되며 따로 지정도 가능하다.
저장 용량을 초과한 객체들이 들어오면 자동적으로 늘어나며, 고정도 가능하다.
동기화(Synchronization)를 제공하지 않는다.

```java
List<E> list = new ArrayList<E>();
```

### Vector

List의 후손으로, 기본적으로 ArrayList와 동등하지만
동기화( Synchronize)를 제공한다는 점이 ArrayList와 차이점이다.
따라서 List 객체들 중에서 **가장 성능이 좋지 않다.**

### LinkedList

List의 후손으로, 인접 참조를 링크해서 체인처럼 관리한다.
특정 인덱스에서 객체를 제거하거나 추가하게 되면 바로 앞/뒤 링크만 변경하면 되기 때문에
객체 삭제와 삽입이 **빈번하게 일어나는 곳에서는 ArrayList보다 성능이 좋다.**
// 새로운 객체가 추가되면 주소만 서로 바꿔주는 작업만 하면 돼서 추가 알고리즘이 간단

```java
public class ListRun{
    public static void main(String[] args){
        
        ArrayList list  = new ArrayList(3);
        
        // 1. 비어있는 list에 추가하기 
		// add(E e) : 해당 리스트의 끝에 인자로 전달된 요소를 추가하는 메소드
        list.add(new Music("애즈잇워즈","해리스타일스"));
		list.add(new Music("기브유어셀프어트라이","일구칠오"));
		list.add(new Music("프리텐더","히게단"));
		list.add("끝"); // 크기가 늘어남, 여러 종류의 값을 담을 수 있음
        // 순서가 유지되면서 저장됨 (index 개념 있음)
        
        // add메소드 사용시 오버로딩된 형태로 사용
        // add(int index, E e) : 리스트의 index 자리에 전달된 e를 추가하는 메소드
        list.add(0, "1");
		list.add(3, new Music("톰보이", "아이들"));
        // 중간에 값 추가시 알아서 기존의 값들을 한 칸씩 밀어주는 작업이 내부적으로 진행됨
        
        // 2. 값 수정
        // set(index, E e) : 리스트의 index자리에 값을 전달된 e로 변경해주는 메소드
        list.set(0, "시작");
		list.set(3, new Music("한", "아이들"));
        
        // 3. 값 삭제
        // remove(int index) : 리스트의 index자리에 담긴 값을 삭제해주는 메소드
        list.remove(0);
		Music tIndex = (Music)list.remove(1); 
        // 인덱스의 값을 잘 고려해서 삭제해야 함
        // IndexOutOfBoundsException : Index 5, 발생!!!
										
        // 4. 리스트의 크기 반환
        // size() : 리스트의 크기를 반환해주는 메소드 == 담겨있는 요소의 갯수
        System.out.println("리스트에 담긴 요소의 갯수 : " + list.size());
		System.out.println("리스트의 마지막 인덱스 번호 : " + (list.size() - 1));
        
        list.remove(list.size() - 1);
        
        // 5. 리스트의 해당 인덱스의 담긴 요소를 반환해주는 메소드
        // get(int index) : E
        Music m = (Music)list.get(0);
        // 반환형이 오브젝트 타입이니까 다형성을 적용해서 강제형변환을 해줘야 함 
        // 다형성 -> 강제형변환
        
        // 향상된 for문 => 값을 조회하는 목적으로 사용이 가능
		// for(값을 받아줄 변수 : 순차적으로 접근할 배열 또는 컬렉션)
		for(Object o : list) {
			System.out.println(o);
		}
        
        // 6. 리스트의 부분만 추출
        // subList(int index1, int index2) : List
		// index1부터 index2까지의 데이터값들을 추출해서 새로운 리스트로 반환시켜준다.
        List sub = list.subList(1, 2);
		System.out.println(sub);
        
        // 7. 리스트 + 리스트
		// addAll(Collection c) : 
		// 해당 리스트에 다른 컬렉션에 있는 데이터들을 통째로 추가해주는 메소드
		list.addAll(sub);
		System.out.println(list); // 데이터(Value)의 중복 저장 가능
        
        // 8. 리스트가 비어있는지 확인하는 메소드
		// isEmpty() : 비어있으면 true / 채워져있으면 false 반환
		System.out.println(list.isEmpty());
        
        // 9. 해당 리스트를 통째로 비워주는 메소드
		// clear()
		list.clear();
		System.out.println(list.isEmpty());
        
    }
}
```



# Generics 제네릭스

### 제네릭스란?

jdk 1.5 부터 제공되는 기능으로, 컬렉션 클래스를 이용해서 객체를 저장할 때, 
**저장할 객체(클래스타입)을 제한하는 기능**으로, **한 가지 종류의 클래스만 저장할 수 있게 해놓은 기능**이다.

### 제네릭스를 사용하는 이유

- '컴파일 단계'에서 '잘못된 타입 사용할 수 있는 문제' 제거함
- 컬렉션에 저장된 여러 종류의 객체를 꺼내서 사용할 때, 객체의 종류에 따라 매번 형변환을 해야 하기 때문에 코드가 복잡해지기 때문
- 컬렉션, 람다식(함수적 인터페이스), 스트림, NIO에서 널리 사용함
- 제네릭스를 모르면 API Document 해석이 어렵기 때문에 학습에 제한

### 제네릭스의 이점

- 컴파일 시 강한 타입 체크가 가능하다. (실행시 컴파일시 에러 방지)
- 타입 변환 제거가 가능하다. (== 헝변환을 하지 않아도 됨)

```java
List list = new ArrayList();
list.add("hello");
String str = (String)list.get(0);
```

​			↓

```java
List<String> list = new ArrayList<String>();
list.add("hello");
String str = list.get(0);
```

### 제네릭 타입

타입을 파라미터로 가지는 클래스와 인터페이스 선언시 클래스 또는 인터페이스 이름 뒤에 "<>" 부호를 붙이고 사이에는 타입 파라미터가 위치한다.

```java
// 클래스명<클래스타입> 레퍼런스 = new 생성자<클래스타입>();
ArrayList<Book> list = new ArrayList<Book>();
```

















