---
layout: post
title: "[도커] 도커파일 명령어"
date:   2019-01-23 00:00:00
description:  도커파일 명령어  # Add post description (optional)
img: docker.jpg # Add image post (optional)
categories: Jiho
tags: [Blog, IT, TypeScript, Angular]
navigation: True
subclass: 'post tag-IT tag-Docker'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/docker.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다. 

이번에 포스팅할 내용은 도커 파일에 사용하는 명령어에대해서 포스팅하겠습니다.
아래 명령어 순서로 포스팅하겠습니다.  

**순서**
>* FROM
>* RUN
>* EXPOSE
>* ENV
>* ENTRYPOINT
>* CMD
>* ADD
>* COPY
>* WORKDIR
>* VOLUME
>* USER
>* LABEL
>* ARG

**1. FROM**  
`FROM` 명령어는 사용할 이미지를 지정하는 명령어입니다. ubuntu, node와같은 이미지파일을 지정합니다. 지정할때는 `:`뒤에 특정 버전을 지정하여 사용할 수 있습니다.
{% highlight ruby %}
FROM ubuntu:18.04
or
FROM node
{% endhighlight %}  

**2. RUN**  
`RUN` 명령어는 내려받은 이미지에 설치할 패키지 또는 shell 명령어를 입력할 수 있습니다. 
예를들어 내려받은 node이미지에 typescript를 설치하는 명령어를 내리고 싶다면
{% highlight ruby %}
RUN npm install -g typescript:[version]
or
RUN ["npm", "install", "-g", "typescript:[version]"]
{% endhighlight %}  
보통 apt-get과 같은 명령어를 이용하여 패키지 설치 명령어를 지정해줍니다.  

**3. EXPOSE**  
`EXPOSE` 명령어는 실행한 container외부에 노출할 포트를 지정하는 명령어입니다.
하지만 container를 실행할때 -p 옵션을통해 연결해주어야한다.
{% highlight ruby %}
EXPOSE 8080
{% endhighlight %}  

**4. ENV**   
`ENV` 명령어는 환경변수를 지정하는 것으로 파일내부에서 변수처럼 활용이 가능합니다.
{% highlight ruby %}
ENV test 123
CMD echo $test
{% endhighlight %}  
해당 도커파일을 빌드하여 실행하면 test변수의 값인 123이 출력되는 것을 확인 할 수 있습니다.
해당 환경변수는 빌드된 이미지를 실행할때 override할 수 있습니다.  

**5. ENTRYPOINT**  
`ENTRYPOINT` 명령어는 컨테이너를 실행했을때 실행할 명령입니다. 컨테이너를 정지했다가 다시 시작해도 실행하는 명령어입니다. 물론 run명령어로 컨테이너를 실행했을때도 실행됩니다.  
컨테이너가 실행될떄 실행되는 명령어이므로 도커파일에서 한번만 사용할 수 있습니다.
{% highlight ruby %}
ENTRYPOINT ["npm", "run", "serve"]
{% endhighlight %}  

**6. CMD**  
`CMD` 명령어는 docker run 실행 시 사용할 default 명령을 설정하는데 사용합니다. 
{% highlight ruby %}
CMD ["npm", "run", "serve"]
{% endhighlight %}  

[ENTRYPOINT와 CMD의 차이][entry_cmd]를 설명하는 사이트입니다.  

**7. ADD**  
`ADD` 명령어는 빌드 중 호스트의 디렉토리에서 파일을 가져와서 이미지에 파일을 더하는 것입니다. 
주의할점은 빌드되는 디렉토리 밖에 위치하는 파일들은 가져오지 않습니다.  
ADD 호스트파일위치 이미지파일위치
{% highlight ruby %}
ADD test.txt /
{% endhighlight %}  
호스트의 test.txt파일이 이미지 파일에 / 위치로 더해집니다.  

**8. COPY**  
`COPY` 명령어는 ADD와 동일한 동작을 합니다. 하지만 압축파일을 자동으로 풀어주지 않습니다.
{% highlight ruby %}
COPY test.txt /
{% endhighlight %}  

**9. WORKDIR**  
`WORKDIR` 명령어는 cd의 명령어와 비슷합니다. RUN과 CMD과 같은 명령어가 실행될 이미지 내부에 위치를 지정해주는 명령어입니다.  
{% highlight ruby %}
WORKDIR /app/
{% endhighlight %}  

**10. VOLUME**  
`VOLUME` 명령어는 호스트의 디렉토리를 docker 컨테이너에 연결하는 명령어입니다. 
여러가지 설정파일, 데이터 등을 docker 컨테이너에너 사용할 수 있게 해줍니다. 
즉 디렉토리 내용을 컨테이너에 저장하지 않고 호스트에 저장하도록 설정하는 것입니다.
로그 수집과 같은 데이터 저장에 쓰임.
VOLUME 호스트디렉토리 컨테이너디렉토리
{% highlight ruby %}
VOLUME ["/data", "/var/log"]
{% endhighlight %}  

**11. USER**  
`USER` 명령어는 해당 docker 이미지를 실행할 user를 지정하는 명령어입니다.
{% highlight ruby %}
USER user
or
USER [uid]:[gid]
{% endhighlight %}  

**12. LABEL**  
`LABEL` 명령어는 이미지에 라벨을 다는 것입니다.
{% highlight ruby %}
LABEL "abcd@gmail.com"
{% endhighlight %}  

**13. ARG**  
`ARG` 명령어는 도커파일 빌드시에 설정하는 옵션들을 지정할 수 있는 명령어 입니다. 
{% highlight ruby %}
ARG arg1
ARG arg2=value
{% endhighlight %}  
위와 같이 지정할 경우 도커파일 빌드시 arg1 인자를 입력받아야합니다. 또한 arg2의 default값은 value값으로 지정되어 빌드된됩니다. 

지금까지 **도커파일 명령어**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[entry_cmd]:http://pyrasis.com/book/DockerForTheReallyImpatient/Chapter07/06