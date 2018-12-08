---
layout: post
title: "Eclipse에서 spring 환경 설정 [Spring]"
date:   2018-12-08 00:00:00
description: Eclipse에서 spring 환경 설정 [Spring] # Add post description (optional)
img: java.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, SPRING, JAVA]
navigation: True
subclass: 'post tag-IT tag-SPRING tag-JAVA'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/java.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다.    

이번에는 **Eclipse에서 Spring 초기 설정**에 대해서 포스팅하겠습니다. 

**순서**
>1. spring plugin install
>2. spring mvc project 생성
>3. tomcat 설치 후 서버 실행
>4. 프로젝트 실행
>5. 한글 인코딩 문제 해결

**1. spring plugin install**  
먼저 Eclipse에서 Spring plugin을 설치하도록 하겠습니다.   
Help -> Market places -> sts검색 -> spring mvc plugin 설치
여기서는 spring plugin 3.x 버전으로 하겠습니다. 

<img src="/assets/images/2018-12-09-eclipse-spring-setup/spring1.png">
위 이미지처럼 간단히 검색하여 spring plugin을 쉽게 설치 할 수 있습니다.

**2. spring mvc project 생성**  
다음으로는 Spring mvc project 생성하는 방법입니다. 
File -> new -> other -> spring -> spring legacy project를 통해 프로젝트를 생성해줍니다. 
<img src="/assets/images/2018-12-09-eclipse-spring-setup/spring2.png">
프로젝트 생성이 완료되었습니다.
<img src="/assets/images/2018-12-09-eclipse-spring-setup/spring5.png">  

**3.tomcat 설치 후 서버 실행**  
이제는 구동 시킬 tomcat서버를 설치하도록 하겠습니다.   
File -> new -> other -> server -> server를 통해 server프로젝트를 생성하시면 됩니다. 
이떄 주의점은 맞는 tomcat 버전서버를 미리 받으셔야합니다.
[tomcat][tomcat] 설치 주소입니다. 접속하셔서 알맞는 버전을 받으시면 됩니다.

<img src="/assets/images/2018-12-09-eclipse-spring-setup/tomcat1.png">
서버가 잘 생성이 된다면 아래와 같은 구조로 생성됩니다.
<img src="/assets/images/2018-12-09-eclipse-spring-setup/tomcat2.png">

**4. 프로젝트 실행**  
이제 tomcat서버를 실행 시키고 만들었던 spring 프로젝트를 실행해보도록 하겠습니다. 

실행이 잘 된다면 아래와 같은 화면이 보여질것입니다.
<img src="/assets/images/2018-12-09-eclipse-spring-setup/spring3.png">

만약 404에러가 발생한다면 spring프로젝트를 실행시킬때 프로젝트 폴더내에서 파일을 실행시키지 않았는지 확인 하셔야합니다.  
spring 프로젝트를 실행시킬떄는 project최상위 폴더에서 프로젝트를 실행시켜야 404 에러없이 위와 같은 화면을 보실 수 있습니다.

**5. 한글 인코딩 문제 해결**   
하지만 화면을 보시면 한글 인코딩 문제로 한글이 깨지는 것을 확인하실수 있습니다.   
이제 해당 문제를 해결해보겠습니다.  
`src -> main -> webapp -> resources -> WEB-INF -> views -> home.jsp`
spring 프로젝트내에서는 home.jsp가 디폴트로 생성되어있을것입니다. 물론 home.jsp가 스프링 실행 첫 화면입니다.
home.jsp에서 해당 코드를 삽입해줍니다.

{% highlight ruby %}
<%@ page language="java" contentType="text/HTML;charset=UTF-8" pageEncoding="UTF-8" %>
<%
request.setCharacterEncoding("UTF-8");
%>
{% endhighlight %}

다음으로
`src -> main -> webapp -> resources -> WEB-INF -> web.xml`
web.xml파일에 해당 내용을 추가해줍니다.
{% highlight ruby %}
	<filter>
                <filter-name>encodingFilter</filter-name>
                <filter-class>
                        org.springframework.web.filter.CharacterEncodingFilter
                </filter-class>
                <init-param>
                        <param-name>encoding</param-name>
                        <param-value>UTF-8</param-value>
                </init-param>
	</filter>
	<filter-mapping>
	        <filter-name>encodingFilter</filter-name>
	        <url-pattern>/*</url-pattern>
	</filter-mapping>
{% endhighlight %}

위에 두개의 설정 코드를 입력하신 후 프로젝트 재시작을 하시면 
아래와 같이 한글이 잘 나오는 것을 확인하실수 있습니다.
<img src="/assets/images/2018-12-09-eclipse-spring-setup/spring4.png">

여기까지 eclipse에서 spring 초기 환경 설정에대해서 포스팅했습니다.   
물론 sts 에디터라와 spring boot와 같이 초기에 쉬운 설정을 할 수 있는 방법들이 있지만 
기존에 방식대로 설정하는 방법이었습니다. ㅎㅎ   
   
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 
같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[tomcat]:http://tomcat.apache.org/