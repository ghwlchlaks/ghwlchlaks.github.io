---
layout: post
title: "[Node.js] 리눅스에서 Node.js 설치"
date:   2018-10-11 22:00:00 +0300
description:  리눅스에서 Node.js 설치 # Add post description (optional)
img: nodejs.png # Add image post (optional)
categories: IT
tags: [Blog, IT, Linux, Node]
author: Jiho # Add name author (optional)
---
안녕하세요! **Do My Best 블로그** 여덟번째 게시물입니다. ㅎㅎ  
오늘은 우분투 운영체제 환경에서 Node.js를 설치하는 방법에 대해서 알아보겠습니다.!

[nodejs-github][nodejs-github]과 [nodejs공식페이지][nodejs-org]을 보시면 잘 설명 되어있습니다. 

**데비안(Debian)과 우분투(Ubuntu)에서 설치하는 방법.**
{% highlight ruby %}curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
{% endhighlight %}

`Node.js 10를 사용하고 싶다면 다음을 실행합니다.`
{% highlight ruby %}curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -  
sudo apt-get install -y nodejs  
{% endhighlight %}  

추가적으로  
**RHEL, CentOS, Fedora에서 설치하는 방법**도 간단하게 설명하겠습니다
{% highlight ruby %}curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash -  
sudo yum -y install nodejs  
{% endhighlight %}

`Node.js 10를 사용하고 싶다면 다음을 실행합니다.`
{% highlight ruby %}curl --silent --location https://rpm.nodesource.com/setup_10.x | sudo bash -  
sudo yum -y install nodejs  
{% endhighlight %}

설치가 아주 간단하죠?ㅎㅎ  

{% highlight ruby %}node -v  
npm -v  
{% endhighlight %}  
해당 명령어로 nodejs와 npm이 잘 설치 되었는지 확인합니다.  

간단하게 예제 코드를 보도록 하겠습니다!   
**app.js**를 생성한 후  

{% highlight ruby %}console.log("Hello world");  
{% endhighlight %}  
해당 내용을 작성 후 저장합니다. 

{% highlight ruby %}node app.js  
#=> Hello world  
{% endhighlight %}  
해당 결과 값이 출력되면 됩니다!!  

이번엔 **간단한 웹서버**를 만들어보겠습니다.  
Node.js가 다른 웹서버와 다른 장점 중 하나는 빠르게 웹서버를 만들 수 있는것입니다!ㅎㅎ  
**app.js**코드를 수정하도록 하겠습니다.    
{% highlight ruby %}var http = require('http');

var server = http.createServer(function (req, res) {
  res.writeHead(200, { 'Content-Type' : 'text/plain' });
  res.end('Hello World');
});

server.listen(3000);
{% endhighlight %}  
해당 내용을 작성 후 

{% highlight ruby %}node app.js  
{% endhighlight %}    
를 실행하게 되면 간단하게 **웹서버가** 실행이 됩니다.  
물론 기능을 더 넣으려면 코드를 추가 해야겠죠?  
웹 서버가 실행이 됐는지 확인하는 방법은 http://127.0.0.1:3000으로 접속하시면 화면에 Hello World가 출력 되는 것을 확인 하실 수 있습니다.!

지금까지 **리눅스에서 Node.js설치 방법**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[nodejs-github]:https://github.com/nodesource/distributions
[nodejs-org]:https://nodejs.org/ko/download/package-manager/