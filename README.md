# Java-Study

## core Java

* ### jdk - jdk 1.8 window 64 bit
	+ jdk => jdk(compiler) + jre(executor)   
			└ 코드가 자바규칙을 잘 지켜서 작성되었는지 확인하고 byte code로 변환.
	+ jre => jre(executor)

* ### API (Oracle.com SE8 API), 편집기 (eclipse neon3)

* ### java.lang 패키지 - 자바의 가장 기초적인 클래스들이 모여있는 곳. 
		 기초자료형의 wrapper 클래스가 존재.
		 클래스의 method를 이용하여 문자와 숫자간 형변환이 가능.
	+ #### 문자   
		+ 문자열 - String: immutable character strings (default value: null)
		+ 문자 - char: ASCII code로 작성된 2byte(0을 포함한 정수) 문자 데이터.   
				(default value: 빈문자열 '\u0000')
	+ #### 숫자
		+ 정수 (default value: (int) 0)
			1. byte: -128 ~ 127까지 표현가능한 1byte 데이터. (default value: (byte) 0)
			2. short: 2byte 데이터. 필요에 따라 사용. (default value: (short) 0)
			3. int: -2³¹ ~ 2³¹-1까지 표현가능한 4byte 정수.   
				특별한 경우를 제외하고는 기본적으로 int형만 사용.   
				int가 아닌 정수형은 사용될 때 int형으로 변형되는 경우가 있음.
			4. long: 8byte 데이터. 숫자 뒤에 L을 붙임. 필요에 따라 사용. (default value: 0L)
		+ 실수 (default value: (double) 0.0)
			1. float: 4byte의 실수. long보다 더 큰 숫자를 표현 가능. 숫자 뒤에 F를 붙임. (default value: 0.0F)
			2. double: 8byte의 default 실수. 숫자뒤에 D 생략 가능. (default value: 0.0D)
	+ #### 논리 (boolean): 1byte (default value: false)
		+ false: 거짓을 표현.
		+ true: 참을 표현.
	+ #### system: 콘솔을 통해 사용자가 데이터를 입출력.
		+ in: Scanner 클래스와 함께 사용하여 사용자에게 데이터를 입력받을 수 있음.
		+ out: print문을 활용하여 콘솔에 데이터를 출력할 수 있음.
		+ err: print문을 활용하여 error message를 출력할 수 있음.
	+ #### thread: process의 작업단위. cpu상에서 처리.
		+ start(): thread를 생성하고 run()을 실행.
		+ run(): thread의 작업을 정의. 종료되면 thread는 소멸.
		+ sleep(long millis): millis / 1000초 만큼 thread를 중지시킨 후, 재실행.
* ### java util 패키지
