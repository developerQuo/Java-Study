# Java-Study

## core Java

* ### jdk - jdk 1.8 window 64 bit
	+ jdk => jdk(compiler) + jre(executor)   
		* compiler: 코드가 자바규칙을 잘 지켜서 작성되었는지 확인하고 byte code로 변환.
	+ jre => jre(executor)

* ### API (Oracle.com SE8 API), 편집기 (eclipse neon3)

* ### java.lang 패키지
	<pre>
	자바의 가장 기초적인 클래스들이 모여있는 곳. 
	기초자료형의 wrapper 클래스가 존재.
	클래스의 method를 이용하여 문자와 숫자간 형변환이 가능.</pre>
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
	+ Date: Date <=> Calendar 변환할 줄 알아야 함.
		+ Date: 날짜를 년, 월, 일, 시, 분, 초 단위로 읽는 클래스.   
			1970년 1월 1일 00시 시간부터 사용. (epoch time: 하루를 정확히 24시간(86,400초)으로 계산)   
			1,900을 더해야 현재 연도가 나옴.
		+ Calendar: 날짜를 년, 월, 일, 시, 분, 초 단위로 읽고 날짜간의 계산 또한 다루는 클래스.   
				(Gregorian calendar: 양력. 1년을 365.2425일로 계산)
	+ Collection Framework: 객체들을 그룹짓는 속성이 있음. Iterable.   
				generic을 사용해서 그룹내 객체들의 데이터타입을 통일할 수 있음.
		+ List: sequence & duplicatable
		+ Set: unduplicatable & 수학의 집합과 동일.
		+ Map: unduplicatable key & at most one value (사전과 유사)
* ### java.sql 패키지: 데이터베이스와의 연결을 위한 자원 가짐.
	+ DriveManager: 적합한 JDBC드라이버를 찾고 연결하는 클래스.
	+ Connection: 연결된 상태(session이 열림). 쿼리를 실행할 수 있음.   
			결과값 반환은 Connection이 유지된 상태에서 가능.
	+ Statement: 쿼리를 실행할 때마다 컴파일해서 사용.
	+ PreparedStatement: 쿼리문을 precompiled해서 사용.   
	Statement <-> PreparedStatement: 적은 양의 쿼리를 처리할 때는 Statement가 더 빠르지만 대량의 쿼리를 처리할 때는 PreparedStatement가 빠름.
	+ ResultSet: a DB result set. cursor 속성이 있어, Iterable.
* ### java.io 패키지
	<pre>
	물리적 파일의 입출력에 관련된 자원을 가짐. 
	io 클래스를 사용하고나면 반드시 close()함수로 닫아야 함.
	사용 시 가능하면 null로 초기화하고, 사용하고 나서도 null로 재초기화 하는 것이 좋음.</pre>
	+ FileOutputStream: 1 byte 단위로 파일을 writing.
	+ FileInputStream: 1 byte 단위로 파일을 reading.
	+ FileReader: 2 byte 단위로 파일을 reading.
	+ FileWriter: 2 byte 단위로 파일을 writing.
	+ Buffered ~: 하나씩이 아닌 한덩어리씩 데이터를 주거나 받음.   
			하나의 덩어리가 완전히 채워지면 차례차례 전송. 전송 단위가 더 큼.
	+ BufferedOutputStream, BufferedWriter, FileOutputStream, FileWriter와 같이 파일을 작성하는 클래스는 아직 채워지지않은 마지막 덩어리(buffer)를 처리하기 위해 __반드시 flush()함수를 사용__.
* ### java.Net 패키지: networking 구현 관련 자원을 가짐.
	+ Inet4Address : IPv4 (networking protocol. 32-bit address space : 2³²)
	+ Inet6Address : IPv6 (networking protocol. 128-bit address space : 2¹²⁸)   
	URI: 특정 자원을 명확하게 가리키는 문자열. (URN: URI 하위의 name space)     
	URL: 자원을 찾기 좋은 정보로 구성 => 문자열. URI의 일종. (호스트이름 + 위치)
* ### 생성자 (Constructor)
	<pre>
	클래스의 객체를 생성할 때의 지침서.
	인스턴스 변수 초기화에 관여.
	클래스에 생성자를 정의하지 않으면 JVM이 기본생성자를 생성.</pre>
	+ 생성자 overloading: 생성자의 시그니처에서 매개변수가 다르다면 개수 제한없이 생성자를 여러 개 정의할 수 있음.
	+ this 키워드: 멤버변수와 parameter가 같은 이름을 사용한다면, 멤버변수에 this 키워드를 사용하여   
			멤버변수와 parameter를 구분해야 함.
	+ inheritance: 상속 관계일 때, 별도로 부모클래스의 생성자를 호출하지 않으면 JVM이 부모클래스의 기본 생성자를 호출.   
			생성자 호출 순서는 자식클래스 생성자 호출 -> 부모클래스 생성자 호출   
					-> 부모클래스 생성자 호출 완료 -> 자식클래스 생성자 호출 완료
	+ 인스턴스를 생성하고 new 키워드를 사용한 경우에 주소값을 가짐.
	+ 인스턴스를 생성하면서 인스턴스 변수를 각 데이터타입의 default 값으로 초기화.   
		인스턴스 변수를 초기화해서 사용해도 되지만 지양하도록 함.
	```
	// 지향
	class initVar {
		int a;
	}

	// 지양
	class initVar2 {
		int a = 1;
	}
	```
	+ 배열의 경우, 인스턴스하면 기초자료형 및 String 배열도 default 값으로 초기화 됨.
* ### flow control
	+ if: 조건식 결과(parameter)가 참이면 if 블럭(scope)를 시행.   
				거짓이면 else 블럭을 시행. 만약 else 블럭이 없으면 if 블럭만 건너뛰고 다음 라인을 시행.
		+ short-circuit evaluation: 논리연산에서 첫 번째 조건이 부합하지 않으면 두번째 조건은 평가되지 않는다.
			- AND연산자일 경우: 첫 번째 조건이 false => false
			- OR연산자일 경우: 첫 번째 조건이 true => true
		+ 데이터 유효성 검증: 데이터를 처리하는 로직에 데이터가 들어오지 않았다면 로직을 실행하지 않도록 데이터 유효성 검증에 조건식을 사용할 수 있다.
	+ for: 조건식 결과(parameter)가 true이면 true가 아닐 때까지 for문 블럭(scope)을 반복 시행.   
		__삼중 이상의 for문 작성은 지양.__
		+ 실행순서: 패턴을 따라 순차적으로 데이터를 처리한다.
			1. 연산자 초기화.		ex) int i = 0;
			2. 조건문 확인		ex) i <= 10;
			3. scope 내용 실행		ex) {System.out.println("i >>> " + i);}
			4. 증감연산자 실행		ex) i++   
			b ~ d 반복. 조건이 false가 되면 scope를 더 이상 실행하지 않는다.
		+ Iterator 함수, while 문, 재귀함수 등이 유사한 기능을 수행.
	+ while: 조건식 결과(parameter)가 조건에 부합하면, 조건이 false가 될 때까지 scope를 반복. 무한루프를 사용할 때 유용.
		+ break: 강제로 반복문(for문, while문)을 빠져나가는 키워드.   
			if문과 함께 사용해서 어떤 조건이 되면 강제로 빠져나갈 수 있다.
		+ continue: continue 다음 라인을 모두 건너뛰고, scope의 마지막으로 이동.   
				자바에서는 가능한 사용을 지양한다.
		+ do-while: 조건을 확인하고 scope의 코드를 시행하는 것이 아니라, 반대로 scope의 코드를 시행하고 난 뒤 조건을 확인.
	+ switch: 조건문.
		+ case: switch문의 매개변수가 조건에 해당하는 경우, 해당 case문의 scope를 시행.   
			단, break문을 scope 마지막에 사용하지 않으면 멈추지 않고 코드를 계속 읽어 내려간다.
		+ break: switch문을 빠져나가는 키워드.
		+ default: 어느 조건에도 해당하지 않을 경우 실행하는 scope.