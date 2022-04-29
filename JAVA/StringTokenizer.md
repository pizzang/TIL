```java
// 문자열을 분리시키는 방법
	
	// 1. 구분자를 제시해서 해당 문자열을 분리시키는 방법 => 배열이용
	// 2. 분리된 각각의 문자열을 토큰으로 취급하는 방법 => 토큰이용
	
	String str = "포켓몬빵, 훌루훌루, 낼모레시험, Java";
	
	// 방법 1
	public void method1() {
		// 문자열.split(String 구분자) :  String[]
		String[] arr = str.split(",");
		
		/*
		for(int i=0; i<arr.length; i++) {
			System.out.println(arr[i]);
		}
		*/
		
		// 향상된 for문 : 초기식; 조건식; 증감식이 필요없다!!!!
		// [ 표현법 ] for(값을 받아줄 변수 선언 : 순차적으로 접근할 배열){	}
		for(String s : arr) {
			System.out.println(s);
		}
		// 출력만 가능 String:arr ???
		// 배열의 값을 수정할 수는 없음 //필기놓침

	}
	
	
	// 방법 2.
	public void method2() {
		
		// 각각의 문자열을 토큰으로 처리
		// java.util.StringTokenizer 클래스를 이용하는 방법
		// [ 표현법 ]
		// StringTokenizer stn = new StringTokenizer(문자열, 구분자);
		// 객체 생성
		
		StringTokenizer stn = new StringTokenizer(str, ",");
		
		System.out.println("분리된 문자열의 갯수 : " + stn.countTokens());
		
		// countTokens() 분리된 문자열의 갯수를 반환해주는 메소드
		
		// 그러면 실제로 분리된 내용물을 보고 싶다면???
		
		/*
		System.out.println(stn.nextToken());
		System.out.println(stn.nextToken());
		System.out.println(stn.nextToken());
		System.out.println(stn.nextToken());
		
		// 그러면 이제 남아있는 토큰이 없을텐데???
		// 또 nextToken()을 호출하면???
		System.out.println(stn.nextToken());
		*/
		
		// NoSuchElementException
		// 더이상 꺼내올 토큰(요소)가 없어서 발생하는 오류
		
		// 반복문
		
		while(stn.hasMoreTokens()) {
			// hasMoreTokens() :
			// stn 남아있는 토큰이 있다면 true
			// 토큰이 다 빠져있으면 false
			
			System.out.println(stn.nextToken());
		}
	}
```

