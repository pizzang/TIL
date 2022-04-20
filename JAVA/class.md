## Field 필드

- 클래스를 구성하는 요소 중 하나

- 어떠한 데이터를 저장하기 위한 역할(변수)

- 클래스 내부지만 메소드 밖의 영역에 정의함

```java
접근제한자 예약어(생략가능) 자료형 필드이름;
```

```java
private String name;
private int age;
private char gender;
```



#### 변수 구분

- **필드** : 클래스 영역에 바로 선언하는 변수
- **지역변수** : 클래스 영역 내 특정한 구역 => 메소드, for문 같은
  for(int i = 0; 조건식; 증감식) {  } => 변수 i가 지역변수



#### 1. 전역변수

- **클래스 변수 (static 변수)** : static이라는 예약어가 붙은 변수
  생성시점 : 프로그램 실행과 동시에 메모리 static 영역에 할당
  			=> 해당 객체가 생성이 되지 않더라도 무조건 프로그램 실행과 동시에 할당이 됨
  소멸시점 : 프로그램이 끝날 때 소멸
  
  - static "공유"의 개념이 강함. (재사용성)
  
  - 프로그램 실행과 동시에 메모리 영역에 공간을 만들어두고 그 안에 값을 공유해서 쓰자!

```java
public static String sta = "static 변수";
```



- **멤버 변수 (인스턴스 변수, 필드)** 
  생성시점 : new 키워드를 사용하면 해당 객체를 생성하는 순간 메모리 영역에 할당 됨
                      => heap 영역
  소멸시점 : 객체가 소멸될 때 => 가비지컬렉터\



#### 2. 지역변수

생성시점 : 특정한 구역 ({	}) 실행 시 메모리 영역에 할당 => stack 영역

소멸시점 : 특정한 구역 ({	}) 종료 시 소멸

```java
public class FieldTest1{
    private int global; //멤버변수(인스턴스 변수, 필드)
    
    public void test(int num){ 
    int local = 0; //지역변수:초기화 꼭 해줘야 함.//필드:초기값이 들어있음.
    
    System.out.println(global); //멤버변수, 필드
    System.out.println(local);  //지역변수
    System.out.println(num);    //매개변수(지역변수에 포함)
    }  
}
```

#### 상수 필드

한 번 지정한 값을 고정해서 쓰겠다 => 그래서 무조건 초기화 해줘야 됨
예약어 순서는 상관 없음

값이 변경되어서는 안되는 고정적인 값을 메모리상(static)에 올려놓고
(프로그램 시작과 동시에 메모리 영역에 할당, 값이 변하지도 않음)
공유할 목적으로 사용

상수필드 이름은 항상 모두 대문자여야 함

```java
public static final 자료형 상수필드이름 = 값;
public final static 자료형 상수필드이름 = 값;
```



#### **필드에서 사용가능한 접근제한자 4가지**

(+) **public** => 어디서든(같은 패키지, 다른 패키지 모두) 접근 가능

(#) **protected** => 같은 패키지면 무조건 접근 가능
								다른 패키지면 상속 구조인 클래스에서만 접근 가능

(~) **default** => 오로지 같은 패키지에서만 접근 가능, 생략 가능

(-) **private** => 오직 해당 클래스 안에서만 접근 가능

+,	#,	~,	-	:	클래스 다이어그램 표기 방법



## Constructor 생성자

###### 객체를 생성할 때 항상 실행되는 것으로 객체를 초기화해주기 위해 처음 실행되는 메소드

메소드 이름이 클래스 이름과 동일하고 리턴자료형이 없는 메소드 (반환형이 없음)

```java
public 클래스이름(매개변수){//매개변수 생략가능
    해당 생성자를 통해서 객체 생성 시 실행하고자 하는 코드
}
```



#### **생성자를 작성하는 목적** 

1. 객체를 생성해주기 위한 목적
2. 객체를 생성 뿐만 아니라 매개변수로 전달된 값들을 바로 필드에 초기화 할 목적

#### **생성자의 종류**

1. 매개변수가 없는 생성자 => 기본생성자
2. 매개변수가 있는 생성자

차이점 : 필드에 값을 초기화 할 수 있냐 없냐의 차이

#### 생성자 작성 시 주의사항

1. 생성자의 이름은 클래스의 이름과 동일해야 함
2. 반환형이 존재하지 않음. 즉 return값 없음. (메소드랑 유사하게 생겨서 헷갈릴 수 있음)
3. 클래스에는 반드시 생성자가 존재해야 함
4. 인스턴스 생성 시 딱 한번 호출됨
5. 생성자가 여러 개 생성 가능하지만 매개변수랑 중복이 되면 안됨 -> 오버로딩
6. 기본생성자는 생략해도 오류가 나지 않음
7. 매개변수 생성자를 명시적으로 작성하게 되면 기본생성자를 JVM이 안 만들어줌



## Method 메소드

기능을 구현하는 부분
입력을 가지고 어떤 일을 수행한 다음에 결과물을 내놓음

```java
접근제한자 예약어 반환형 메소드이름(매개변수){//예약어, 매개변수 생략가능
	수행할 코드;
    return 반환값; //반환형이 void일 경우 생략가능
}
```

**생략 가능한 것** : 예약어, 매개변수, return문 부분(반환형이 void일 경우)

```java
public void method(){
    
}
```

**접근제한자** : 호출할 수 있는 범위를 제한

**반환형** : 메소드의 결과값의 자료형을 지정해줌 || void → 돌려줄 값이 없다.

**매개변수** : 메소드 호출 시 입력값으로 넣어주는 변수.
					해당 메소드 실행중에만 사용 가능한 변수. 생략가능

호출할 때 인자 값 => 매개변수의 자료형과 갯수가 일치해야 함

한 번 정의해두고 필요할 때마다 호출해서 사용 가능



- #### setter() / getter() 메소드

**setter() 메소드** : 데이터를 기록 및 수정하는 기능의 메소드

1. setter메소드는 접근 가능하도록 만들어야 하기 때문에 public 접근제한자를 이용
2. set필드명으로 짓기, camelCase를 지키기
3. 모든 필드에 대해서 전부 다 작성해주기

**getter() 메소드** : 데이터를 반환해주는 기능의 메소드

1. getter메소드는 접근제한자 public 사용
2. get필드명으로 짓기, camelCase 지키기
3. 모든 필드에 대해서 전부 다 작성해주기



#### 1. 매개변수 X 반환값 X 

```java
public void method1(){
    System.out.println("매개변수 X 반환값 X");
    
    int sum = 0;
    for(int i=0; i<=10; i++){
        sum+=i;
    }
    System.out.println(sum);
    //return;
    //void일 경우 return생략. JVM이 자동으로 만들어줌
}
```

#### 2. 매개변수 X 반환값 O

```java
public int method2(){
    System.out.println("매개변수 X 반환값 O");
    
    return (int)(Math.random() * 100) + 1;
}
```

```java
MethodTest1 mt1 = new MethodTest1(); //static메소드면 생략 가능

int a = mt1.method2();
System.out.println("랜덤값 : " + a);
System.out.println("랜덤값 : " + mt1.method2());
//값을 가지고 돌아옴
//랜덤값을 사용하고 싶으면 변수에 담던지 아니면
//출력구문을 만들어줘야 함
```

#### 3. 매개변수 O 반환값 X

```java
public void method3(int num1, int num2){
    System.out.println("매개변수 O 반환값 X");
    
    int min = 0;
    int max = 0;
    
    if(num1 < num2){
        max = num2;
        min = num1;
    }else {
        max = num1;
        min = num2;
    }
    System.out.println("최소값 : " + min + ", 최대값 : " + max);
}
```

#### 4. 매개변수 O 반환값 O

```java
public int method4(int a, int b){
    System.out.println("메개변수 O 반환값 O");
    
    return a+b;
}
```

```java
MethodTest1 mt1 = new MethodTest1(); //static메소드면 생략 가능

int b = mt1.method4(a, 50); //2. 매개변수 X 반환값 O에서 선언한 변수 a
		System.out.println(b); 
```

#### // static 매개변수 X 반환값 O

```java
public static String method2(){
    return "매개변수 X 반환값 O";
}
```

```java
MethodTest2.method2();
//값을 가지고 돌아옴. 문장을 사용하고 싶으면 변수에 담던지 or 출력구문 필요
System.out.println(MethodTest2.method2());
```



#### // static 매개변수 O 반환값 X

```java
public static void method3(String name, int age){
	System.out.println("매개변수 O 반환값 X");
	System.out.println(name + age);
}
```

```java
MethodTest2.method3("유저1", 22);
```

반환형이 없는 메소드 : 출력문을 작성하는 편
반환형이 있는 메소드 : 호출하는 부분에서 출력문을 작성



#### Overloading 메소드 오버로딩

- 한 클래스 안에 같은 메소드 명으로 여러 메소드들을 정의할 수 있는 방법
- 매개변수의 자료형의 갯수, 순서, 종류가 다 다르게 작성되어야 함
- 단, 매개변수명, 접근제한자, 반환형은 메소드 오버로딩에 영향을 주지 않음

```java
public void test(){
    System.out.println("매개변수 X");
}
public void test(int a){
    System.out.println("int a 하나만 받음");
}
public void test(int a, String s){
    System.out.println("int a 먼저, String s 두번째로 받음");
}
public void test(String s, int a){
    System.out.println("String s 먼저, int a 두번째로 받음");
}
public void test(int a, int b){
    System.out.println("int a 먼저, int b 두번째로 받음);
}
```

매개변수의 이름과는 상관없이 자료형의 갯수, 순서가 같으면 에러 발생

```java
public void test(int c, int d){ //에러; 위 코드에 int a, int b 있음
    
}
```

