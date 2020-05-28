# Spring_Study

#GIT

이클립스에서 터미널 사용법
	
	 Step1)
	메뉴 : [Window] >> [Show View] >> [Other...] >> [Terminal] >> [Terminal] 선택 >> [Open]  
	
	Step2)
	[Terminal] 아이콘 클릭 >> Terminal 창의  [Open a Terminal] 아이콘 클릭 >>  Choose terminal 에서 Git Bash 선택 후 사용
	
Git 명령어
------------

	$git init
	- 현재 디렉토리를 git 저장소로 등록된다.
	
	$git add -all 
	- 현재 디렉토리 및 그 하위에 있는 모든 파일들을 git의 변경 대상으로 등록한다. 하기전에 아래  .gitignore 파일에 쓸데없는 파일들을 먼저 정리하는것을 추천함.
	
	.gitignore
	- 이 파일에 만약 git을 통해  관리하기 싫은 파일이 있다면 기록해둔다. 
	
	$git commit 
	- git add 명령을 통해 등록된 파일들을 커밋한다. git add / rm 되지 않은 파일들은 커밋 대상에 포함되지 않는다. 
	
	$git commit -a
	- git add 명령을 통해 이전에 등록해둔 파일들의 변경(modified, deleted)된 내역들을 자동으로 커밋한다.
	
	$git commit file1 file2 file3 
	- 지정된 특정 파일들만 커밋한다.
	
	$git commit -m'commit message'
	- 커밋 로그를 작성하지 않고 -m 명령에 붙은 메시지를 커밋 로그로 반영한다. 
	
	
	
	
자바 스프링 프레임워크- 신입 프로그래머를 위한 강좌 
-------------
[제1강]
-------------	
	스프링 프레임워크는 주요기능으로 DI, AOP, MVC, JDBC 등을 제공

	spring-core  : 스프링의 핵심인 DI와 IoC를 제공
	spring-aop   : AOP구현 기능 제공
	spring-jdbc  : 데이터베이스를 쉽게(적은 양의 코드) 다룰 수 있는 기능 제공
	spring-tx    : 스프링에서 제공하는 트랜잭션 관련 기능 제공
	spring-webmvc: 스프링에서 제공하는 컨츠롤러와 뷰를 이용한 스프링MVC구현 기능 제공

[제2강 - 개발 환경 구축]
-------------	
	JDK설치 후 Eclipse 설치 
	--skip

[3강 - 스프링 프로젝트 생성]
-------------	
	1) 생성
	오른쪽 마우스 클릭 -> New -> Other-> maven 검색 -> Maven project 생성
	Group id 	: 전체 큰 프로젝트를 감싸고 있는 이름
	Artifact id : 현재 만들고있는 프로젝트 이름

	2) 설정 
	pom.xml

	3) 폴더
	src/main/java
	: 실제로 자바 언어를 이용해서 기능 구현을 하는 부분
	src/main/resources
	: 자바 프로그래밍을 해 나감에 있어서 여러가지 보조역할을 하는 부분
	
	4) 폴더 및 pom.xml 파일의 이해
	pom.xml 파일은 메이븐 설정파일로 메이븐은 라이브러리를 연결해주고, 빌드를 위한 플랫폼이다. 
	
	5) 에러 
	-- 메이븐 업데이트 시키면 오류 사라짐
	
[4장 - 처음해보는 스프링 프로젝트]
-------------
	1) Spring Container 
	<bean id="아이디 속성" class = "패키지명(풀네임). java 파일 명"/>
	 --> new라는 키워드를 사용하지 않아도 객체가 생성됨(메모리에 로드)

	2) 컨테이너 접근 방법 
	GenericApplicationContext ctx = new GenericApplicationContext("classpath:applicationContext.xml");
	ctx.getBean("tWalk", TransportationWalk.class ); : 컨테이너 안에 있는 bean을 가져옴	 

[6장 - DI(Dependency Injection]
-------------

	1) DI는 무엇인가?
	-  객체를 직접 생성하는 것이 아니라 외ㅏ부에서 생성한 후 주입을 시켜주는 방식 
	

[7장 - 다양한 의존 객체 주입]
-------------	
	
1) 생성자를 이용한 의존 객체 주입
```
public StudentRegisterService(StudentDao studentDao){
	this.studentDao = studentDao;
}

public StudentModifyService(StudentDao studentDao){
	this.studentDao = studentDao;
}

.xml
<bean id="registerService" class="ems.member.service.StudentRegisterService">
	<constructor-arg ref="studentDao"></constructor-arg>
</bean>

<bean id="modifyService" class="ems.member.service.StudentModifyService">
	<constructor-arg ref="studentDao"></constructor-arg>
</bean>
```
2) setter을 이용한 의존 객체 주입
```
public void setJdbcUrl (String jdbcUrl){
	this.jdbcUrl = jdbcUrl;
}
public void setUserId(String userId){
	this.userId = userId;
}
public void setUserPw(String userPwd){
	this.userPwd = userPwd;
}

.xml
<bean id = dataBaseConnectionInfoDev" class= "ems.member.DataBaseConnectionInfo">
	<property name="jdbcUrl" value="jdbc:oracle:thin:@localhost:1521:xe"/>
	<property name="userId" value="scott"/>
	<property name="userPwd" value="tiger"/>
</bean>
```
3) List타입의 의존 객체 주입 
```
public void setDevelopers(List<String> developers){
	this.developers = developers;
}

.xml
<property name="developers">
	<list>
		<value>Cheney.</value>
		<value>Eloy.</value>
		<value>Jasper.</value>
		<value>Dillon.</value>
		<value>Kian.</value>
	</list>
</property>
```
4) Map타입 객체 주입
```
public void setAdministrators(Map<String,String> administrators){
	this.administrators = administrators;
}

.xml 
<property>
	<map>
		<entry></entry>
		<key>
			<value>Cheney</value>
		</key>
			<value>cheney@springPjt.org</value>
		<key>
			<value>Jasper</value>
		</key>
			<value>jasper@springPjt.org</value>
	</map>
</property>
```







