---
layout: post
title: "[도커] 도커파일 Typescript node App에 도커파일 만들기"
date:   2019-01-24 00:00:00
description:  도커파일 Typescript node App에 도커파일 만들기  # Add post description (optional)
img: docker.jpg # Add image post (optional)
categories: Jiho
tags: [Blog, IT, TypeScript, Node]
navigation: True
subclass: 'post tag-IT tag-Docker tag-Node'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/docker.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다. 

이번에 포스팅할 내용은 도커 파일을 작성하여 자신이 개발한 Typescript용 node를 이미지로 만드는 방법에대해서 포스팅하겠습니다. 

먼저 Dockerfile에 명령어가 알고싶다면 [링크][dockerfile-instruction] 를 클릭해주세요!

**Dockerfile**  
Dockerfile을 자신이 개발한 앱폴더안에 넣어 작성합니다.  
아래방법은 예시방법중 하나입니다. 자신의 개발한 환경에 맞게 작성해주셔야합니다.  
{% highlight ruby %}
FROM node:version
# 특정 버전 node 이미지를 받아옵니다.  
MAINTAINER choi
# 작성자의 이름을 적습니다. 
WORKDIR /app
# 만들 이미지에 작업할 디렉토리로 이동합니다.  
COPY package*.json /app/
# 현재 디렉토리에 package로 시작하는 파일들을 복사하여 이미지에서 작업할 디렉토리로 복사합니다. 
RUN npm install
# 이미지 디렉토리에서 npm install 명령어를 실행해 줍니다. 
# package.json이 있으므로 npm install로 종속 모듈이 설치가 되겠죠?  
RUN npm install -g typescript
# typescript를 이용한 node이므로 전역옵션을 이용하여 typescript 모듈을 설치해줍니다.  
COPY ./ /app/
# 현재 폴더에 있는 모든 파일들을 복사하여 이미지 디렉토리에 복사합니다. 
# 여기과정이 자신이 작성한 코드등 리소스들이 복사됩니다.  
RUN npm run build-ts
# typescript로 작성된 node이므로 build를 하여 javascript 파일로 컴파일 해줍니다.  
CMD ["npm", "run", "serve"] 
# 해당 이미지가 실행될때 실행될 명령어입니다. 
# 해당 이미지를 컨테이너로 실행할때 npm run serve 명령어가 실행되어 자신이 작성한 코드에 node가 실행됩니다.                      
{% endhighlight %}  

지금까지 **Typescript node App에 도커파일 만들기**이라는 주제로 포스팅하였습니다!     

해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[dockerfile-instruction]:https://ghwlchlaks.github.io/dockerfile-instruction