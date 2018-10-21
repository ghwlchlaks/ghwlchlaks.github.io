---
layout: post
title: "[Node.js] 정적(static) 파일 import (css, image)"
date:   2018-10-09 00:00:00 
description: 정적(static) 파일 import (css, image) [Node.js] # Add post description (optional)
img: nodejs.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Language, Node]
navigation: True
subclass: 'post tag-IT tag-Language tag-Node'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/nodejs.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 여섯번째 게시물입니다. ㅎㅎ  
지금까지 파이썬 언어에대해 포스팅 해왔는데요..   
사실 파이썬은 알고리즘 공부땜에 파이썬 언어로 공부하며 알고리즘공부도 하고 있습니다. 

이번에는 서버 프레임워크 중 하나인 **Node.js의 static경로 설정 방법**에 대해 포스팅하도록 하겠습니다.   
제가 전에 경로땜에 살짝 헤맸다는...

막상 포스팅을 시작하려니 Node.js의 개념에대해 먼저 포스팅을 했어야했다는 것이 생각이나네요..  
아직 블로그 초보라..하하..  
다음에는 Node.js 개념에대해 포스팅하도록 하겠습니다.!

Node.js에서 **static**경로를 설정하는 방법에대해서 알아 보아요~  
여기서는 기본적으로 **express-generator**로 생성한 Node.js 폴더라는 가정하에 다루도록하겠습니다.!  

Node를 사용하면서 ejs나 pug 등과 같은 확장자를 만질때가 있을텐데요~  
자신이 추가하고자하는 외부 css파일이나 image파일을 Node.js 폴더내에 추가하고 
view에서 접근하여도 css나 image가 적용이 되지 않는 당황스러운 경험을 하실 수 있는데요~  
이때 css와 image가 적용이 되지않는 문제를 해결해보도록 하겠습니다!

Node.js폴더내에 app.js를 확인해보면~   
{% highlight ruby %}
app.use(express.static(path.join(__dirname, '../public')));
{% endhighlight %}  
이러한 코드를 확인 하실 수 있을것입니다!
이코드는 express-generator로 생성한 폴더라면 default로 설정되어있습니다.  

해당 코드의 의미는 정적(static)한 파일을 이곳에 넣어두면 `/` 경로로 ejs파일내에서 public폴더내에 있는 파일을 접근 할 수 있다는 의미입니다. 

예를들어 `/public/test.jpg` 라는 파일이 **public 폴더**내에 존재한다면
ejs파일내에서 `src=/test.jpg `로 접근을 할 수 있습니다.!!

만약 default로 설정된 `/` 경로가 아닌 다른 정적(static) 폴더를 만들고 다른 경로를 만들어서 사용하고 싶으시다면 app.js 파일에  
{% highlight ruby %}
app.use('/ejs에서접근할경로', express.static(path.join(__dirname, ' /실제위치한디렉토리경로')));  
{% endhighlight %}

해당 코드를 입력하고~  
**ejs**에서 `src=/ejs에서접근할경로/정적(static)파일위치` 로 접근하시면
image,css와같은 파일들의 자원을 사용하실 수 있습니다!!

한번 테스트해보시고 사용해보시면 좋을것같습니다.!  
지금까지 **Node.js에서 정적(static)** 파일 사용하는 방법이었습니다!  
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  
