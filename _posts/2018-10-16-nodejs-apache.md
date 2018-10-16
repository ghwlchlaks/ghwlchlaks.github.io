---
layout: post
title: "Node.js 와 Apache 연동"
date:   2018-10-16 12:00:00 +0300
description:  Node.js 와 Apache 연동 # Add post description (optional)
img: nodejs.png # Add image post (optional)
categories: IT
tags: [Blog, IT, Node, Linux, Apache]
author: Jiho # Add name author (optional)
---
안녕하세요! **Do My Best 블로그**입니다. ㅎㅎ  
이번 포스팅 부터는 횟수를 세지 않았습니다!

이번에 포스팅할 내용은 **Node.js 서버와 Apache서버를 Proxy**를 사용하여 연동하는 방법에대해 알아보겠습니다.

proxy를 사용하여 apache로 들어온 정보를 node.js에게 전달해주는 방식입니다. 

* **필요한 apache모듈 활성화**
* **가상 호스트 설정**
  
## **1. 필요한 apache모듈 활성화.**  
먼저 mod_proxy, mod_proxy_http가 설치되어있어야합니다. 하지만 ubuntu에서 apache서버는 기본적으로 모듈이 설치되어있습니다. 

처음에는 두개의 모듈이 비활성화 되어있을겁니다.  
활성화를 하는 방법은 
{% highlight ruby %}
sudo a2enmod proxy  
sudo a2enmod proxy_http  
{% endhighlight %}   
명령어를 사용하여 활성화 해줍니다. 

## **2. 가상 호스트 설정.**  
* /etc/apache2/sites-available폴더로 이동합니다.   
* 해당 폴더에 들어가서 000으로 시작하는 파일 내용을 수정합니다. 만약 새롭게 파일을 만들고 싶다면 파일을 cp명령어로 복사를 한 후 `e2sites '파일이름'`으로 등록을 해주어야 합니다.   
* 새롭게 파일을 등록 한 후 확인하려면 sites-enabled 폴더 안에softLink로된 같은 파일이 잘 등록 되어있는지 확인합니다. softLink파일인지 확인하는 방법은 `ls -l` 명령어를 입력하였을 떄 
lrwxr-xr-x 1 test test 5 Mar 7 22:00 link1 -> file1  
위와 같이 맨앞에 `l`문자와 `->`기호가 있으면됩니다. 우분투에서는 파일이 초록색으로 나오네요?ㅎㅎ  
* 해당 파일의 내용을 작성해봅니다.!  
  
{% highlight ruby %}

<VirtualHost *:80>  
#The Server Name directive sets the request schema, hostname and port that  
#the server uses to identify itself. This is used when creating  
#redirection URLs. In the context of virtual hosts, the ServerName  
#specifies what hostname must appear in the request's Host: header to  
#match this virtual host. For the default virtual host (this file) this  
#value is not decisive as it is used as a last resort host regardless.  
#However, you must set it for any further virtual host explicitly.  
#ServerName www.example.com  

ServerAdmin webmaster@localhost  
DocumentRoot /var/www/html  

#Available loglevels: trace8, ..., trace1, debug, info, notice, warn,  
#error, crit, alert, emerg.  
#It is also possible to configure the loglevel for particular  
#modules, e.g.  
#LogLevel info ssl:warn  

ErrorLog ${APACHE_LOG_DIR}/error.log  
CustomLog ${APACHE_LOG_DIR}/access.log combined  

#For most configuration files from conf-availalbe/, which are  
#enabled or disabled at a global level, it is possible to  
#include a line for only one particular virtual host. For example the  
#follwing line enables the CGI configuration for this host only  
#after it has been globally disabled with "a2disconf".  
#Include conf-available/serve-cgi-bin.conf  
  
ProxyPass /url http://localhost:3000/url
{% endhighlight %}    
`ProxyPass`부분을 보시면 됩니다. `ProxyPass 접속url nodejsurl` 이러한 형식으로 설정을 계속 추가해 보시면 웹에서 접속url에 접근하였을때 nodejsUrl로 전달해주는 방식이 됩니다.!  
`service apache restart` 이후 apache를 재시작 해주시면 설정이 적용됩니다!!

생각외로 간단합니다! 하지만 안해보면 모른다는.. 한번 테스트 해보시면 좋을것 같네요~

지금까지 **Node.js 와 Apache 연동 방법**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  
