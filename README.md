# Spring_Study

자바 스프링 프레임워크- 신입 프로그래머를 위한 강좌 

[제1강]
	스프링 프레임워크는 주요기능으로 DI, AOP, MVC, JDBC 등을 제공

	spring-core  : 스프링의 핵심인 DI와 IoC를 제공
	spring-aop   : AOP구현 기능 제공
	spring-jdbc  : 데이터베이스를 쉽게(적은 양의 코드) 다룰 수 있는 기능 제공
	spring-tx    : 스프링에서 제공하는 트랜잭션 관련 기능 제공
	spring-webmvc: 스프링에서 제공하는 컨츠롤러와 뷰를 이용한 스프링MVC구현 기능 제공

[제2강 - 개발 환경 구축]
	JDK설치 후 Eclipse 설치 
	--skip

[3강 - 스프링 프로젝트 생성]
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

[4장 - 처음해보는 스프링 프로젝트]








