---
layout: post
title: "[Node.js] 윈도우에서 Node.js 설치"
date:   2018-10-13 22:00:00
description:  윈도우에서 Node.js 설치 # Add post description (optional)
img: nodejs.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Window, Node]
navigation: True
subclass: 'post tag-IT tag-Window tag-Node'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/nodejs.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 아홉번째 게시물입니다. ㅎㅎ  
이번에 포스팅할 내용은 여덟번째 내용이었던 [리눅스에서 Node.js 설치][linux-installation-nodejs]에 이어 윈도우 운영체제 환경에서 Node.js를 설치하는 방법에 대해서 알아보겠습니다.!

**1. Node.js [공식 사이트][node-org]에 접속하기.**
접속하시면 자신의 운영체제에 맞게 페이지가 등장합니다!  
![node-org-pic]({{site.baseurl}}/assets/img/node-org.png)  
해당 페이지에서 LTS버전을 클릭하여 윈도우 node.js 설치 파일을 다운받습니다!

**2. 설치 진행**
설치 파일을 더블클릭하여 윈도우에서 Node.js 설치를 진행합니다.
특별한 설정을 할 이유가 없으면 계속해서 Next를 클릭하여 진행합니다!

<img src="/assets/images/2018-10-13-nodejs-installation-window/node-window-installation-step1.png">

  

<img src="/assets/images/2018-10-13-nodejs-installation-window/node-window-installation-step2.png">



여기서는 nodejs 폴더를 지정해줍니다. default로 해둬 상관이없다면 **Next!**  
<img src="/assets/images/2018-10-13-nodejs-installation-window/node-window-installation-step3.png">



<img src="/assets/images/2018-10-13-nodejs-installation-window/node-window-installation-step4.png">



설치가 완료되고 나면 아까 폴더 경로를 설정한 위치로 이동합니다!  
<img src="/assets/images/2018-10-13-nodejs-installation-window/nodejs-folder.png">
잘 설치된 것을 확인하시면됩니다.!

설치가 너무 쉽죠? ㅎㅎ

**3. 예제 코드 실행!**  
이제 예제 소스를 실행해 잘 설치가 되었는지 확인해 봅시다!
app.js를 만들어 전에 사용했던 예제소소를 여기서도 이용해보겠습니다.!

{% highlight ruby %}console.log("Hello world");  
{% endhighlight %}  
해당 내용을 작성 후 저장합니다.   

<img src="/assets/images/2018-10-13-nodejs-installation-window/node-example.png">

위에 사진처럼 생성되면 됩니다!

이후 해당파일을 실행해 보겠습니다.
cmd를 이용하여 해당 파일의 경로로 이동 후 `node app.js`로 해당파일을 실행할 수 있습니다.!  
결과는 역시 **Hello world**겠죠?

이번엔 **간단한 웹서버**를 만들어보겠습니다.  
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

하지만 항상 cmd로 접속하여 경로를 찾고 실행시키면 번거롭겠죠?  
자신이 자주 사용하는 에디터에 콘솔 기능으로 쉽게 실행 시킬 수 있습니다.   
저는 VSCode를 사용하는데요 콘솔기능이 있어 에이터 안에서 서버를 실행 시킬 수 있어 편리하답니다!
여러분들도 자신이 주로 사용하는 에디터에서 쉽게 접근해 사용해보세요!!

지금까지 **윈도우에서 Node.js설치 방법**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[linux-installation-nodejs]:https://ghwlchlaks.github.io/nodejs-installation-ubuntu/
[node-org]:https://nodejs.org/