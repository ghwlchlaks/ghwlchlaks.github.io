---
layout: post
title: "[리눅스] GUI, CLI 환경으로 변경 방법"
date:   2019-01-21 00:00:00
description: GUI, CLI 환경으로 변경 방법 # Add post description (optional)
img: linux.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, TypeScript, Angular]
navigation: True
subclass: 'post tag-IT tag-Linux'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/linux.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다. 

이번에 포스팅할 내용은 리눅스 GUI환경에서 CLI환경으로 바꾸는 방법에대해서 포스팅하겠습니다.
바꾸는 방법은 한가지 파일만 수정하면 되므로 쉽습니다.  
순서는 아래와 같습니다.  

**순서**
>* 주석 처리
>* 수정
>* 주석 제거
>* CLI 환경 적용
>* GUI 환경으로 돌아가기 

이번 포스팅은 /etc/default/grub 파일만을 다룹니다.  

**1. 주석 처리**
{% highlight ruby %}
GRUB_CMDLINE_LINUX_DEFAULT 라인을 주석처리합니다.
{% endhighlight %}  
<img src="/assets/images/2019-01-21-linux-gui-to-cli/1.png">  

**2. 수정**
{% highlight ruby %}
GRUB_CMDLINE_LINUX 라인을 GRUB_CMDLINE_LINUX="text" 로 수정합니다.
{% endhighlight %}  
<img src="/assets/images/2019-01-21-linux-gui-to-cli/2.png">

**3. 주석 제거**
{% highlight ruby %}
\#GRUB_TERMINAL=console' 라인에 주석을 제거하여 'GRUB_TERMINAL=console' 로 수정
{% endhighlight %}  
<img src="/assets/images/2019-01-21-linux-gui-to-cli/3.png">  

여기까지 파일 수정은 끝이났습니다. :wq명령어 혹은 쓰시는 에디터의 명령어를 이용하여 저장하고 빠져나옵니다.  

**4. CLI 환경 적용**
아래 명령어를 이용하여 적용해줍니다. 

{% highlight ruby %}
systemctl set-default multi-user.target
{% endhighlight %}  
<img src="/assets/images/2019-01-21-linux-gui-to-cli/5.png">  

**4. GUI 환경으로 돌아가기**
혹시나 GUI환경으로 돌아가려면 아래와같은 명령어를 실행해줍니다. 
{% highlight ruby %}
systemctl set-default graphical.target
{% endhighlight %}  
<img src="/assets/images/2019-01-21-linux-gui-to-cli/4.png">  

이제 모든 설정이 끝이 났습니다. reboot를해서 재부팅을 하면 CLI환경으로 접속되는것을 확인 할 수 있습니다.

지금까지 **GUI, CLI 환경으로 변경 방법**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  
