---
layout: post
title: "[Angular] Angular 프로젝트 생성"
date:   2019-01-08 00:00:00
description: Angular 프로젝트 생성  # Add post description (optional)
img: nodejs.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Node, TypeScript, Angular]
navigation: True
subclass: 'post tag-IT tag-Node tag-TypeScript tag-Angular'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/nodejs.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다. 

이번에 포스팅할 내용은 Angular 프로젝트 생성을해서 실행까지 해보도록 하겠습니다. 

이번 포스팅은 Node가 설치되어 있는 상태라 가정하고 진행하도록 하겠습니다.  
node가 설치 되지 않은 분들은 아래 링크에 들어가셔서 자신에 운영체제에 맞게 설치를 진행하시면 되겠습니다.  
[윈도우 설치][window-node-install]  
[리눅스 설치][linux-node-install]

**순서**
>* Angular cli 설치 및 Angular 새로운 프로젝트 생성
>* Angular 실행

**1. Angular cli 설치 및 Angular 새로운 프로젝트 생성**
{% highlight ruby %}
npm install -g angular-cli
{% endhighlight %}  
전역(g)옵션으로 angular 명령어를 사용할 수 있는 라이브러리를 설치해 줍니다. 
설치가 되고나면 angular-cli는 ng 명령어 키워드를 이용할 수 있습니다. 

이제 angular 프로젝트를 생성해 보겠습니다. 아주 간단합니다.
{% highlight ruby %}
ng new [project name]
{% endhighlight %}  
<img src="/assets/images/2019-01-08-angular-starter/newProject.png">
그러면 위 이미지처럼 선택하는 항목이 나오게되는데 위에 이미지가 default입니다. 
css말고 scss등 선택할 수 있습니다. 

선택하시면 쉽게 프로젝트가 생성되었습니다.

**2. Angular 실행**
이번에는 만들어진 default 프로젝트를 실행해 보도록하겠습니다. 
ng 명령어 키워드를 이용하시면 됩니다. 
{% highlight ruby %}
ng serve
{% endhighlight %}  

<img src="/assets/images/2019-01-08-angular-starter/startPage.png">
서버가 실행이되면 `localhost:4200`에 접속하시게되면 위 이미지와같이 출력되는것을 확인 하실 수 있습니다. 


다음 링크는 초기 환경 설정이 된 github link 입니다. 

[Angular-starter][Angular-starter]

지금까지 **Angular 프로젝트 생성**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[Angular-starter]:https://github.com/ghwlchlaks/angular-bulletinBoard-example/tree/env/angular-material
[linux-node-install]:https://ghwlchlaks.github.io/nodejs-installation-ubuntu/
[window-node-install]:https://ghwlchlaks.github.io/nodejs-installation-window/