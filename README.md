<div id="til" />

# TIL (Today I Learn)
# Index
1. [IoC / DI](#ioc-/-di)
2. [Spring](#spring)
3. [Servlet & Spring](#servlet-&-spring)
4. [Spring vs Spring Boot](#spring-vs-spring-boot)

***
# IoC / DI
> IoC (Inversion of Control)
+ Spring 에서만 쓰이는 용어가 아님
+ 개발자가 직접 객체를 생성하여 코드를 제어하면 절차적
-> IoC는 개발자가 직접 코드를 제어하지 않고 Spring 에서는 Spring Container 에게 역할을 위임한다.
+ 코드 흐름이 제 3자에게 위임되는 것을 IoC 모델이라고 한다.

*이점*
+ IoC 프로그램 모델은 곧 역할과 책임에 분리라는 이점이 있다
+ 역할과 책임의 분리는 객체지향 프로그래밍의 핵심 내용
+ 변경에 유연한 코드 구조를 가져가기 위해서 역할과 책임을 분리한다

> DI (Dependency Injection)

>   >스프링이 여타 프레임워크와 차별화돼서 제공해주는 기능은 의존관계 주입이라는 새로운 용어를 사용할 때 분명하게 드러난다. 생략…
DI는 오브젝트 레퍼런스를 외부로부터 제공(주입)받고 이를 통해 여타 오브젝트와 다이내믹하게 의존관계가 만들어지는 것이 핵심

>   >By 토비의스프링

+ 외부로부터 객체의 주소(레퍼런스) 값을 전달 받게 되어 객체가 참조 되어지는 방식
+ 핵심은 DI는 클래스타입이 고정되어 있지 않고 인터페이스 타입의 파라미터를 통해 다이나믹하게 구현 클래스를 결정해서 제공 받을수 있어야 한다.

> IoC / DI
+ IoC는 객체의 흐름, 생명주기관리등 독립적인 제 3자에게 역할과 책임을 위임하는 방식에 프로그래밍 모델
+ 디자인패턴에서도 찾아볼수 있고 다른 컨테이너를 가진 프레임워크들에서도 찾아볼 수 있다. 범용적인 표현.
+ 하지만 DI는 인터페이스를 통해 다이나믹하게 객체를 주입을 하여 유연한 프로그래밍을 가능하게 하는 패턴으로 좀 더 구첵적인 의미

[위로](#til)
***
# Spring
> 핵심기술

- 자바 기반의 Framework
- Spring 은 객체지향언어가 가진 강력한 특징을 살려내는 Framework
- *좋은 객체 지향* Application 을 개발할 수 있게 도와주는 Framework

> 좋은 객체지향설계의 5가지 원칙(SOLID)

1. SRP (단일 책임 원칙)
 - Single Reponsibility Principle
 - 변경이 있을 때 파급 효과가 적으면 단일 책임 원칙을 잘 따른 것
2. OCP (개방/폐쇄 원칙)
 - Open/Closed Principle
 - 확장에 열려있고 변경에 닫혀있다
 - 다형성을 통해 기능을 나눌 수 있다
3. LSP (리스코프 치환 원칙)
 - Liskov Substitution Principle
 - 일종의 규약을 벗어가서는 안된다
 - 컴파일을 넘어서서 다형성을 지원하기 위해 인터페이스 규약을 지켜야한다
4. ISP (인터페이스 분리 원칙)
 - Interface Segregation Principle
 - 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다
5. DIP (의존관계 역전 원칙)
 - Dependency Inversion Principle
 - 추상화에 의존해야 하며 구현체에 의존하면 안된다

[위로](#til)
***
# Servlet & Spring
> Servlet vs Spring

Servlet
- HTML 등의 웹 컨텐츠를 생성하고 전달하기 위해 Servlet 클래스의 구현 규칙을 지켜 자바로 만들어진
*프로그램*

Spring
- 자바 엔터프라이즈 개발을 편리하게 해주는 오픈소스, 경량급 Application *프레임워크*
- Servlet 을 구현한다

> CGI, Servlet

*static web page -> dynamic web page*

CGI
- Common Gateway Interface
- http 통신규약을 사용하는 웹서버가 웹 Appication 과 데이터를 주고 받는 처리 *규약*
- 인터페이스이므로 여러언어로 구현이 가능했고, Servlet 이전에는 직접 구현.
- 문제
    - 1Client 1Process, 객체지향X

Servlet
- GCI 를 따르지만 Servlet Container 에게 위임
- Servlet 이 컨테이너 내부에서 *쓰레드 단위*로 요청을 처리하고 생명 주기를 갖는다.
- 흐름은 개발자가 아닌 컨테이너가 제어함(IOC)
- Servlet 은 웹서버 내부에서 동작하는 작은 자바 프로그램
- Servlet 은 일반적으로 HTTP 를 통해 웹 Client 들로부터 요청을 수신하고 응답.
- Servlet 인터페이스를 구현하기 위해선 GenericServlet 을 상속받거나 HttpServlet 을 상속받아 구현한다.

> Spring & Servlet
```
Tamcat 내부에서 상속
- Servlet(interface)
 - GenericServlet
  - HttpServlet
   
   Spring 에서 상속
   - HttpServletBean
    - FrameworkServlet
     - DispatchServlet
```

[위로](#til)
***
# Spring vs Spring Boot

> Spring 생태계

- Spring 은 Spring Boot, Spring Framework, Spring Data, Spring Security 등 여러 프로젝트의 모음.

- 각각의 프로젝트마다 하위 모듈을 가지고 있음.

> Spring Framework 이란?

- 객체 지향의 특징을 잘 활용할 수 있게 해주며, 개발자들은 핵심 비즈니스 로직 구현에만 집중할 수 있게 해주는 프레임워크.

- 비즈니스 로직과 엔터프라이즈 기술을 분리하여 개발자는 객체지향설계 초점을 맞출수있고 스프링은 DI 나 IOC 와 같은 기능을 제공하여 객체지향의 다형성을 극대화 할수 있음.

> Spring Boot 란?

- Spring Boot 는 Spring 기반의 Application 을 쉽게 만들 수 있게 해준다.

- Spring 의 어떤 부분이 불편해서 Spring Boot 가 나왔을까?
    * Spring 은 초기설정을 잘 해놓아햐 하는데 설정이 많아지고 복잡해지면서 쉽지 않은 일이 되어버렸다.(스프링은 설정이 반이라는 말이 있다.)

- Spring Boot 는 약간의 설정만으로 Spring Application 을 만들 수 있게 해준다.

- Spring Boot 는 Spring 프로젝트 중 하나로, Spring Framework 를 쉽게 해주는 도구이지, Spring Framework 와 별개로 사용할 수 있는 것은 아니다.

> Spring Boot 를 사용하면 달라지는 점
1. 의존성관리
    - Spring 은 개발자가 모듈과 버전을 직접 관리했어야했음.
    - Spring Boot 는 spring-boot-starter 를 지원해준다.
    - 자주 사용하게 되는 모듈간의 의존성과 버전 조합을 제공해준다.
2. 자동설정
    - Spring 은 DataSource 나 Template Resolver 등을 세팅해줘야한다. Servlet 3.0 부터는 XML 이 아닌 Java 로 설정할 수 있게 되었지만 그래도 설정을 해줘야한다.
    - Spring Boot 는 설정파일에 datasource 를 간단하게 설정해줄 수 있다.
    
    ```java
    // main
    @SpringBootApplication

    // Spring Boot 전용 어노테이션
    // 스프링 제공 테스트시 없으면 실패
    > @SpringBootConfiguration

    // 자동설정
    > @EnableAutoConfiguration
    >> @Import(AutoConfigurationImportSelector.class)
    ```

3. 내장 WAS
    - Spring 을 통해 웹 Application 을 개발 하고 난후, 배포하려면
    1. Application WAR 패키징
    2. WAS 설치
    3. WAS 에 WAR 올리기
    > 내장 WAS 역시 Spring Boot 의 자동설정으로 올라가는 것이고, Tomcat 이 아닌 다른 WAS 로도 설정할 수 있다. 
4. 모니터링
    - Spring Boot 의 모듈 중 하나인 'Actuator' 는 Application 의 관리 및 모니터링을 지원해준다.
    - 'Actuator' 는 상용 서비스 수준에서 필요로 할 모니터링 기능을 엔드포인트로 미리 만들어서 제공해준다.
    ```
    End Point
    /health : Application 의 상태 정보
    /metrics/{name} : Application 의 metric 정보(system cpu usage, process.file.open 등)
    /beans : 어떤 빈이 등록되어 있는지
    /loggers/{name} : Application 의 로거 구성
    ```
    > *주의*<br>
    actuator 는 민감정보도 제공되기 때문에 Spring Security 등을 이용하여 보안에 신경써줘야한다.<br>
    actuator 의 데이터는 메모리에 쌓이기 때문에 다른 저장소에 저장해주지 않으면 내장 WAS 를 재시작하면 없어진다. 

[위로](#til)