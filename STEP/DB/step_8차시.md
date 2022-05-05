8차시 : 문자열 불변성과 예외처리

# String 클래스

- Immutable (불변이다)
- 문자열 값 수정 못 함
- 수정시 수정된 문자열이 새로 할당되어 새 주소 넘김
- 그러므로 문자열 조작작업에는 부적합함
  (너무 많은 객체가 만들어지게 되므로...)

------

- 한번 기록된 문자열값은 수정 불가능
- 문자열값은  JVM에 의해 관리됨
- 모든 문자열값은 자유메모리영역(heap) 안의 문자열저장소(Literal Pool)에 기록됨
- 문자열저장소는 한 번 기록된 문자열값은 두 번 기록하지 않음



### StringBuffer 클래스  : mutable(변할 수 있다)

- 문자열 내용 수정 가능함 (문자열 조작에 적합)
- 기존 문자열에 수정 적용됨 ( 추가, 삭제 등)
- 버퍼를 이용함 (기본 16문자크기로 지정, 증가)
- 쓰레드  safe 기능을 제공함 (성능저하요인)



### StringBuilder 클래스 : 1.5 부터 제공됨

- StringBuffer 와 마찬가지로 mutable
- StringBuffer 와 생성자, 메소드 동일함
- 쓰레드 safe 기능을 제공하지 않음
- 새로 나온 클래스이므로 구버전과의 호환성을 고려한다면, StringBuffer가 나을 수 있음



### 문자열 분리 처리용 클래스

- java.util.StringTokenizer 클래스
- java.lang.String 클래스의 split() 사용
  : 문자열을 구성하고 있는 특정 문자를 기준으로 문자열들을 조각 내는 것
  - 분리용 특정 문자 == 토큰(Token)
    ** 토큰문자를 제시하지 않으면, 디폴트는 공백문자임.
    디폴트를 제외하고는 어떤 문자이든 토큰으로 사용가능함(기호문자포함)
  - 문자열값이 토큰문자를 구분기호로 여러 개의 문자열로 나뉨
    String => String[ ]





# 예외처리 Exception

### Error 

프로그램 수행시 치명적 상황이 발생하여 비정상 종료 상황이 발생한 것을 에러 Error라고 한다.



### Error의 종류

**컴파일 에러** : 소스 상의 문법 Error, 소스 구문을 수정하여 해결함

**런타임 에러** : 입력 값이 틀렸거나, 배열의 인덱스 범위를 벗어났거나, 계산식의 오류 등으로 인해 발생, 주로 if문 사용으로 에러에 대한 처리

**시스템 에러** : 컴퓨터 오작동으로 인한 에러 : 소스 구문으로 해결 불가



### Error 해결 방법

소스로 해결 가능한 에러를 예외 Exception 이라고 한다. 이러한 예외상황(예측 가능한 에러)을 처리하는 방법을 예외처리라고 한다.

> 소스코드로 해결 못하는 에러를 에러로 처리
> 소스코드로 해결 가능한 에러는 예외 Exception로 분류



### Exception 클래스

예외클래스는 소스코드상에서 반드시 개발자가 처리해야 되는 checked exception과 개발자가 소스 코드 상에서 다룰 필요가 없는 unchecked exception 두 부류로 나누어진다.

![image-20220424144305672](C:\Users\김유미\AppData\Roaming\Typora\typora-user-images\image-20220424144305672.png)



### RuntimeException 클래스

Unchecked Exception이며, 주로 프로그래머의 부주의로 인한 bug인 경우가 많기 때문에 Excepton 처리보다는 코드를 수정해야 하는 경우가 많다.



### RuntimeException 후손클래스

##### ArithmeticException

- 0으로 나눈 경우에 발생
- If문으로 먼저 나누는 수가 0인지를 검사해야 함

##### NullPointException

- Null인 ref.변수로 객체 멤버 참조 시도
- 객체를 사용하기 전에 ref.변수가 null인지 먼저 확인해야 함

##### NegativeArraySizeException

- 배열 크기를 음수로 지정한 경우
- 배열 size를 0보다 크게 지정해야 함

##### ArrayIndexOutOfBoundsException

- 배열의 index범위를 넘어서 참조하는 경우
- 배열이름.length를 써서 배열의 범위를 확인해야 함

##### ClassCastException

- Cast연산자 사용시 타입 오류
- Instanceof 연산자를 이용하여, 먼저 객체 타입을 확인 후 Cast연산해야 함



### Exception 확인하기

API Document에서 해당 클래스에 대한 생성자나 메소드를 검색하면, 그 메소드가 어떠한 Exception을 발생시킬 가능성이 있는지 확인할 수 있다. 해당 메소드를 사용하려면 반드시 뒤에 명시된 예외 클래스를 처리해야 함.



### Exception 처리 방법

1. Exception 처리를 호출한 메소드에게 위함

- 메소드 선언시 throws ExceptionName 문을 추가하여 호출한 상위 메소드에게 처리를 위임하여 해결한다.
- 계속적으로 위임하면 main()까지 위임하게 되고, main()까지 가서도 예외처리가 되지 않는 경우 비정상 종료된다.

2. Exception을 발생한 곳에서 직접 처리

- try~catch문을 이용하여 예외를 처리한다.
- try : exception 발생할 가능성이 있는 코드를 try구문 안데 기술한다.
- catch : try 구문에서 exception 발생 시 해당하는 exception에 대한 처리를 기술한다.
  여러 개의 exception처리가 가능하나, exception간의 상속관계를 고려해야 한다.
- Finally : 
  exception 발생 여부에 관계 없이, 꼭 처리해야 하는 logic은 finally 안에서 구현한다.
  중간에 return문을 만나도 finally구문은 실행한다.
  단, System.exit();를 만나면 무조건 프로그램을 종료한다.
  주로 java.io, java.sql 패키지의 메소드 처리시 이용한다.



### throws로 예외 던지기

![image-20220424150118006](C:\Users\김유미\AppData\Roaming\Typora\typora-user-images\image-20220424150118006.png)



### try~catch 표현식

```java
try{
    //반드시 예외 처리를 해야 하는 구문 작성함
}catch(처리해야할예외클래스명 레퍼런스){
    //잡은 예외 클래스에 대한 처리 구문 작성함
}finally{
    //실행 도중 해당 Exception이 발생을 하던,
    //안하던 반드시 실행해야 하는 구문 작성함
}
```

### try~catch 구문 예시

![image-20220424150420890](C:\Users\김유미\AppData\Roaming\Typora\typora-user-images\image-20220424150420890.png)



### try~with~resource 구문

자바 7에서 추가된 기능으로, finally에서 작성되었던 close()처리를 생각하고 자동으로 close처리 되게 하는 문장이다.



### try~with~resource 표현식

```java
try(반드시 close 처리 해야 하는 객체에 대한 생성 구문){
    //예외 처리를 해야 하는 구문 작성함
}catch(처리해야할예외클래스명 레퍼런스){
    //잡은 예외 클래스에 대한 처리 구문 작성함
}finally{
    //실행 도중 해당 Exception이 발생을 하던,
    //안하던 반드시 실행해야 하는 구문 작성함
}
```



### 오버라이딩과 Exception

오버라이딩 시 throws 하는 Exception은 같거나 개수를 줄이거나, 더 구체적인 것(후손)으로 변경할 수 있다.

![image-20220424151306613](C:\Users\김유미\AppData\Roaming\Typora\typora-user-images\image-20220424151306613.png)



### 사용자 정의 예외생성

Exception 클래스를 상속받아 예외 클래스 작성함
Exception 발생하는 곳에서 throw new UserDefinedException()으로 발생

![image-20220424151701014](C:\Users\김유미\AppData\Roaming\Typora\typora-user-images\image-20220424151701014.png)



























