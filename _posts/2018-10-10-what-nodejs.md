---
layout: post
title: "[Node.js] NodeJs란 무엇인가?"
date:   2018-10-10 00:00:00 +0300
description: NodeJs란 무엇인가? [Node.js] # Add post description (optional)
img: nodejs.png # Add image post (optional)
categories: IT
tags: [Blog, IT, Language, Node]
author: Jiho # Add name author (optional)
---
안녕하세요! **Do My Best 블로그** 일곱번째 게시물입니다. ㅎㅎ  
전에 말씀 드렸다시피 오늘은 **NodeJS란 무엇인가?**라는 내용을 포스팅하려고 합니다.

**NodeJS는** 확상성 있는 네트워크 애플리케이션 특히 서버사이드 개발에 
사용되는 소프트웨어 플랫폼입니다.  
작성 언어로 자바스크립트(JavaScript)를 활용하며 Non-blocking I/O와 단일 스레드 이벤트 루프를 통한 높은 처리 성능을 가지고 있습니다.   
그러니 Node.js를 사용하려면 자바스크립트를 알아야겠죠?

**Non-blocking I/O란?**    
기존의 I/O 처리 방법에는 I/O작업을 시작하면 
완료될 때 까지 기다리는 방법으로 수많은 I/O 작업이 있는 경우
I/O 작업이 진행되는 동안 프로그램이 아무일도 하지 않고 시간을 소비하게 만듭니다.   
하지만 Non-blocking I/O방식에서는 입출력 처리는 시작만 해둔 채 완료되지 않은 상태에서 다른 처리 작업을 계속 진행 할 수 있도록 멈추지 않고 입출력 처리를 기다리는 방법을 말합니다!  

내장 HTTP 서버 라이브러리를 포함하고 있어 웹 서버에서 Apache, Nginx 등의 별도의 소프트웨어 없이 NodeJS만으로 동작하는 것이 가능하며 이를 통해 웹서버의 동작에 있어 더 많은 통제를 가능케 합니다.!  

**단일 스레드 이벤트 루프란?**  
하나의 쓰레드(Thread)에서 이벤트 루프를 돌려, 이벤트가 발생하면 해당 되는 함수를 실행시키기 때문에 단일한 Thread로 여러 요청처리가 가능합니다.   
Event Loop는 단일 Thread지만 Thread Pool 내부는 여러개의 Thread를 사용하여 Event Loop가 Callback함수를 내부에 여러 Thread들에게 요청을 할당해 줍니다. 
그리고 작업이 끝난 작업들은 Event Loop가 순차적으로 Event Queue에 할당합니다.

그리고 한개 더 알아야할 것! **비동기**입니다.!  

**비동기란?**  
간단합니다! **순서가 정해지지 않는다** 라는 의미입니다.  
비동기와 Non-blocking 방식이 같다고 생각하시분들이 있으실텐데요!   **의미는 다릅니다.!**  
**Non-blocking 방식**은 입출력처리가 시작되고 완료되지 않은 상태에서 반환하여 다른 처리를 할 수 있도록 하는 것이고,  **비동기 방식**은 어떤 수행이 완료되었을 때 NodeJS의 콜백함수와 같은 신호를 보내 알려주는 것입니다!  
비동기방식에서는 함수를 호출한 쪽에서 처리하지 않고 콜백함수를 통해 처리합니다!

어려운내용이네요..ㅠㅠ 크게 **NodeJS**의 특징에대해서 알아보았습니다. 
그럼 이제 예제를 한번 해보고 마치도록 하겠습니다.  

**NodeJS**는 다른 서버언어와 다르게 간단히 코드 몇줄로 서버를 구성할 수 있습니다. 
아래 예시를 한번 봅시다! ㅎㅎ  
{% highlight ruby %}
var http = require('http');

http.createServer(function (request, response) {
    response.writeHead(200, {'Content-Type': 'text/plain'});
    response.end('Hello World\n');
}).listen(3000);

console.log('Server running at http://localhost:3000/');
{% endhighlight %}


한번 테스트해보시고 사용해보시면 좋을것같습니다.!  
지금까지 **Node.js란?**이라는 주제로 포스팅하였습니다!  
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  
