---
layout: post
title: "Oracle 설치 및 Spring에서 연동 [Oracle]"
date:   2018-12-10 00:00:00
description: Oracle 설치 및 Spring에서 연동 [Oracle] # Add post description (optional)
img: java.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, SPRING, JAVA, DB]
navigation: True
subclass: 'post tag-IT tag-SPRING tag-JAVA tag-DB'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/java.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다.    

이번에는 **Oracle 설치 및 Spring에서 연동**에 대해서 포스팅하겠습니다. 

**순서**
>1. Oracle database 설치
>2. Oracle database 생성
>3. JUnit 설치
>4. JUnit을 이용한 database 연결 테스트

**1. Oracle database 설치**  
먼저 oracle database를 설치하도록 하겠습니다.  
[oracle][oracle] 에 접속하셔서 로그인 하시면됩니다. 만약 계정이 없다면 회원가입 하셔야겠죠?  
회원가입을 하신 후 아래와 같은 화면과 같이 64비트를 클릭하시면 됩니다. 

<img src="/assets/images/2018-12-10-spring-oracle-setup/oracle-setup1.png">

계속해서 다음을 누르면서 설치를 진행합니다.

<img src="/assets/images/2018-12-10-spring-oracle-setup/oracle-setup2.png">

그렇다면 쉽게 oracle database를 설치 하실 수 있습니다. 

**2. Oracle database 생성**  
sql developer.exe를 실행합니다. 
그 후 아래 그림에서 초록색 `+`버튼을 클릭합니다.
<img src="/assets/images/2018-12-10-spring-oracle-setup/oracle-setup3.png">

그렇다면 아래와 같은 창이 표시됩니다. 
<img src="/assets/images/2018-12-10-spring-oracle-setup/oracle-setup4.png">

접속이름, 사용자이름, 패스워드, sid(데이터베이스 이름)를 적절히 입력한 후 생성해 줍니다. 

여기까지 하시면 데이터베이스 설치 부터 생성까지 완료가 되었습니다. 

**3. JUnit 설치**  
이제 이클립스에서 JUnit 라이브러리를 이용하여 데이터베이스가 연결이 잘 되는지 확인해 보겠습니다. 
spring폴더 내에서 `pom.xml`을 열어서 아래와 같이 dependency를 추가해 줍니다. 

{% highlight ruby %}
<!-- Test -->
        <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>4.7</version>
                <scope>test</scope>
        </dependency>
{% endhighlight %}

추가하고 저장한다면 자동으로 이클립스에서 해당 라이브러리를 다운받습니다.   
그러면 JUnit 테스트를 위한 라이브러리가 설치가 끝났습니다. 

**4. JUnit을 이용한 database 연결 테스트**  
이제 테스트 코드를 작성해 보겠습니다.   
spring폴더내에 `src/test/java` 폴더에서 아래와 같이 OracleConnectionTest.java 파일을 생성해 줍니다.
<img src="/assets/images/2018-12-10-spring-oracle-setup/junit1.png">
그리고 파일내에 해당 코드를 작성해 줍니다. 
{% highlight ruby %}
private static final Logger Logger = LoggerFactory.getLogger(OracleConnectionTest.class);
private static final String DRIVER = "oracle.jdbc.driver.OracleDriver";
private static final String URL = "jdbc:oracle:thin:@localhost:1521:orcl";
private static final String USER = "system";
private static final String PW = "1234";

@Test //JUnit이 테스트하는 코드
public void testConnection() throws Exception {
        Class.forName(DRIVER);
        try(Connection conn= DriverManager.getConnection(URL, USER, PW)) {
                Logger.info("오라클에 연결되었습니다.");
        }catch(Exception e) {
                e.printStackTrace();
        }
}
#=> 이때 주의점은 URL에 자신의 데이터베이스 환경에 맞는 ip, port, 데이터베이스 이름 작성
#=> USER, PW에 아까 데이터베이스 생성시에 작성했던 계정아이디 비밀번호를 각각 적어줍니다.
{% endhighlight %}

위와같이 작성해주고 저장해줍니다.   
이제 해당코드를 실행하여 테스트 해보겠습니다.   
OracleConnectionTest.java 파일을 오른쪽으로 클릭하고 `run as`를 보시면 JUnit test가 있을겁니다. 
이것을 클릭하여 실행해봅시다.

그렇다면 아래와같이 에러 없이 작동하는 것을 확인하시면됩니다.
<img src="/assets/images/2018-12-10-spring-oracle-setup/junit2.png">  

그리고 console창을 확인해보겠습니다.  
<img src="/assets/images/2018-12-10-spring-oracle-setup/junit3.png">

위와같이 에러없이 로그 값이 출력된다면 데이터베이스와 연결 테스트가 성공적으로 된 것입니다. 




여기까지 `Oracle 설치 및 Spring에서 연동`에대해서 포스팅했습니다.   
지금까지는 데이터베이스 설치, 데이터베이스 설정, spring과 데이터베이스(oracle) 연결 테스트를 진행했습니다.
   
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 
같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[oracle]:https://login.oracle.com