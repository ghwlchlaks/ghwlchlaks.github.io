---
layout: post
title: "docker-compose apache tomcat, mysql 환경 구성 [docker]"
date:   2018-12-06 00:00:00
description: 간단하게 docker-compose apache tomcat, mysql 환경 구성 [docker] # Add post description (optional)
img: docker.jpg # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Docker, DB]
navigation: True
subclass: 'post tag-IT tag-Docker tag-DB'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/docker.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다.    

이번에는 docker에대해 포스팅하려고 합니다.  
docker에 대한 개념설명을 먼저하려고 했으나 제가 연습한 내용이 있어서 해당 내용을 간단히 먼저 포스팅하려고 합니다. ㅎㅎ

docker를 이용하여 어느 환경에서나 동일한 작업환경을 구성할 수 있는 장점이 있는데요
이때 사용하는 것이 dockerfile, docker-compose 입니다. 

여기서 docker-compose는 여러개의 이미지 파일을 이용하여 여러개의 컨테이너를 실행시켜 동일한 작업 환경을 구축하는데에 사용하기위해 사용하는 파일입니다. ㅎㅎ 

이번 포스팅에서는 apache tomcat, mysql 환경을 구축하는 docker-compose 파일을 작성하는 방법에대해 알아보도록 하겠습니다.

**해결 순서**
>1. docker 설치
>2. docker-compose 파일 작성
>3. docker-compose 파일 실행

간단하죠? ㅎㅎ
사실 설치와 실행은 더 간단합니다. 가장 중요한것은 docker-compose 파일을 작성하는 것입니다.

그럼 실습을 통해서 한번 진행해 보도록 하겠습니다.

**1. docker 설치**  
{% highlight ruby %}
apt-get update
apt-get upgrade
#=> 간단히 리눅스 환경에서 update와 upgrade를 해줍니다. ㅎㅎ
apt-get install curl 
#=> docker를 apt-get으로 설치해도 되지만 curl를 이용해서 설치하기위해 curl를 설치 해줍니다.
curl -fsSL https://get.docker.com/ | sudo sh
#=> curl 명령어를 이용해 docker를 설치 해줍니다.
{% endhighlight %}
간단한 설치 과정으로 1번 과정이 끝이 났습니다.

아래 파일은 [docker-compose-apache-tomcat-mysql][docker-compose-apache-tomcat-mysql] 에서 보실 수 있습니다.  

**2. docker-compose 파일 작성**  
{% highlight ruby %}
version: '2'
services:
        db:
                image: mysql:latest
                environment:
                        MYSQL_ROOT_PASSWORD: 1234
                        MYSQL_DATABASE: test
                        MYSQL_USER: user
                        MYSQL_PASSWORD: 1234
                ports:
                        - "3306:3306"
                volumes:
                        - "./db:/docker-entrypoint-initdb.d"
                restart: always

        web:
                image: tomcat:latest
                environment:
                        JDBC_URL: jdbc:mysql://db:3306/test?connectTimeout=0&amp;socketTimeout=0&amp;autoReconnect=true
                        JDBC_USER: user
                        JDBC_PASS: 1234
                ports:
                        - "80:8080"
                volumes:
                        - ./tomcat/webapps:/user/local/tomcat/webapps
                links:
                        - db
                restart: always  

#=> 1번째: db라는 이름으로 컨테이너를 생성합니다.
#=> 2번째: 최신 버전의 mysql이미지를 다운받습니다.
#=> 3~7번째: db컨테이너에대해 환경설정을 하는 부분입니다.
#=> 8~9번째: host포트와 docker container포트를 연결할 port번호입니다.
#=> 10~11번째: 컨테이너안에서 사용하는 데이터를 host에 저장할 위치입니다. 
#=> 이외에 web도 비슷한 흐름이므로 설명을 생략하겠습니다.
#=> 추가적으로 web에서 links는 연결할 컨테이너 이름입니다. 컨테이너를 연결하여 web에 enviroment등과 같이 설정을 연결할 수 있습니다.
{% endhighlight %}
이외에도 여러가지 옵션이 있고 복잡한 환경설정을 할 수 있지만 기본적으로 환경설정을 할 수 있는 설정파일작성이 끝이 났습니다.   
해당 내용을 `docker-compose.yml`로 저장하고 터미널환경으로 나와 줍니다~ㅎㅎ

**3. docker-compose 파일 실행**  
이제 해당 내용이 잘 작성되었는지 실행해보도록 하겠습니다.
{% highlight ruby %}
docker-compose up
#=> 해당 커맨드를 입력하면 docker-compose.yml파일이 실행이 됩니다. 
#=> 백그라운드로 파일을 시작하고 싶다면 `-d` 옵션을 추가적으로 입력해줍니다.
{% endhighlight %}

실행이 완료되면 docker ps 명령어를 이용하여 db와 web컨테이너가 잘 실행되었는지 확인합니다.
{% highlight ruby %}
docker ps
{% endhighlight %}
<img src="/assets/images/2018-12-07-docker-tomcat-mysql/docker_ps.png">

위에 사진처럼 두개의 컨테이너가 실행이 된것을 확인하시면 됩니다  

여기서는 tomcat과 mysql두개의 컨테이너를 생성하는 커맨드를 docker-compose파일로 작성하였지만 
추가적으로 자신이 개발할 환경에 맞는 커맨드를 이용하여 docker-compose파일을 만든다면 어디서나 똑같은 개발환경을 구축하는데에 편해질것입니다.  

또한 위에 적힌 커맨드 옵션 이외에도 많은 옵션들이 있으니 공부하시면서 테스트 해보시면 좋을 것같습니다. 

지금까지 docker-compse를 이용하여 tomcat, mysql 컨테이너 환경 구축하는 방법에대해 포스팅했습니다.
   
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 
같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[docker-compose-apache-tomcat-mysql]:https://github.com/ghwlchlaks/docker-example-tomcat-mysql