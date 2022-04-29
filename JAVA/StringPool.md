# String

String 클래스 => 불변클래스 (변하지 않는 클래스)
수정하는 순간 기존의 값이 담겨져 있는 공간에서 수정되지 않음

String 클래스 형태의 객체 생성 방법

- new 키워드로 생성자 호출
- 대입연사자를 통해서 직접 값을 넣어서 생성

```java
	// 1. 생성자를 통해서 문자열 담기
	public void method1() {
		String str1 = new String("hello");
		String str2 = new String("hello");
		
		System.out.println(str1.toString());
        System.out.println(str2);
		// 1. String클래스의 toString() 의 경우
		// 실제 담겨있는 문자열을 반환하게끔 오버라이딩이 되어있음
		
		// equals()
		System.out.println(str1.equals(str2));
		// true => 문자열을 비교했는데 동일하다.
		// 2. String클래스의 equals()의 경우
		// 주소값 비교가 아닌 문자열 비교를 하도로 오버라이딩
		
		// hashCode();
		// 16진수의 주소값 => 10진수의 형태
		System.out.println(str1.hashCode());
		System.out.println(str2.hashCode());
		// 3. String클래스의 hashCode()
		// 주소값을 반환해주는 것이 아닌 실제 담긴 문자열을 기반으로
		// 해시코드값을 만들어서 반환
		
		// 진짜 주소값을 알고싶다면?
		// System.identityHashCode(참조변수형);
		System.out.println(System.identityHashCode(str1));
		System.out.println(System.identityHashCode(str2));
		// 실제 주소값의 해시코드를 출력
		// str1과 str2의 주소값이 다르다
		
		// ==
		System.out.println(str1 == str2); //false
    }
```

```java
	// 2. 문자열을 리터럴로 생성
	public void method2() {
		String str1 = "hello";
		String str2 = "hello";
		
		// toString()
		System.out.println(str1);
		System.out.println(str2);
		
		// equals()
		System.out.println(str1.equals(str2)); //true
		
		// hashCode()
		System.out.println(str1.hashCode());
		System.out.println(str2.hashCode());
		
		// System.identityHashCode()
		System.out.println(System.identityHashCode(str1));
		System.out.println(System.identityHashCode(str2));
		//???????? 두개의 찐 주소값이 똑같다 ????????
		
		System.out.println(str1 == str2); //true
		
	}
```

```java
	// String 클래스의 StringPool
	public void method3() {
		
		String str = "hello";
		// 리터럴 대입 시  String pool 영역에 올라감
		// String pool의 특징 : 동일한 내용의 문자열이 존재 불가하다!
		
		System.out.println(System.identityHashCode(str));
		
		str = "goodbye";
		System.out.println(System.identityHashCode(str));
		
		// 연결이 끊긴 문자열들은 가비지컬렉터가 알아서 정리해줌
		// 불변이라고해서 아예 수정이 안되는 것이 아니라
		// 매 번 새로운 주소값을 참조한다라는 뜻

		str += "abc";
		System.out.println(System.identityHashCode(str));
		str += "abc";
		System.out.println(System.identityHashCode(str));
		
		String a = "a";
		String b = "a";
		System.out.println("결과 : " + a == b); //false
		System.out.println("결과 : " + (a == b)); //true
	}
```

```java
public void method4() {
		// StringBuffer
		// 문자열은 안에 내용이 변경될 때마다 새로운 공간을 할당하고 새로 집어넣는다.
		// 이를 막기 위해 임시공간(buffer)을 하나 준비하여
		// 임시공간에 차곡차곡 담아두었다가 한번에 처리해주는 클래스가
		// StringBuffer / StringBuilder 이다.
		
		StringBuffer sb = new StringBuffer();
		
		sb.append("Hello");
		System.out.println("Hello".hashCode());
		System.out.println(sb.hashCode());
		
		sb.append(" World!");
		System.out.println("Hello World!".hashCode());
		System.out.println(sb.hashCode());
		
		System.out.println("결과 : " + sb);
		
		// StringBuffer는 동시제어 기능(Thread Safe)기능을 가진다.
		// 간단한 프로그램 구현이나, 동시제어를 다른 프로그램이 제공하는 경우
		// 굳이.. 버퍼까지?? 동시제어를 구현할 필요는 없다
		// 이 기능만 쏙 뺀 클래스가 필요했는데 그게  StringBuilder다!
	}
```

```java
public void method5() {
		//StringBuilder
		
		StringBuilder sb = new StringBuilder();
		
		sb.append("Hello");
		System.out.println("Hello".hashCode());
		System.out.println(sb.hashCode());
		
		sb.append(" World!");
		System.out.println("Hello World!".hashCode());
		System.out.println(sb.hashCode());
		
		System.out.println("결과 : " + sb);
	}
```

