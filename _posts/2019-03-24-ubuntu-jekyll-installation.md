---
layout: post
title: "리눅스에서 지킬 설치 및 실행 [Jekyll]"
date:   2019-03-24 01:00:00
description: 윈도우에서 지킬 설치 및 실행. # Add post description (optional)
img: github.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Github, Jekyll]
navigation: True
subclass: 'post tag-IT tag-Github tag-Jekyll'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/github.png'
author: Jiho # Add name author (optional)
disqus: true
---
이번에는 리눅스 환경에서 jekyll를 설치하는 방법에대해서 알아보도록하겠습니다.

이번에 노트북을 리눅스 운영체제로 바꾸고 jekyll를 설치해본 경험을 바탕으로 작성하겠습니다.

**1. 루비 (Ruby) 설치!**  
먼저 ruby를 설치 해줍니다.
```
apt-get install ruby-dev
```

**2. 지킬 (Jekyll) 설치**  
jekyll를 설치 해보도록하겠습니다.
```
gem install jekyll
```
역시 리눅스는 간단한 명령어로 패키지를 설치할 수 있는 장점이 있네요 ㅎㅎ

하지만 jekyll 설치 애러가 나타나는 경우가 있습니다. 이때는 의존 소프트웨어를 설치해주어야합니다. 
참고한 [링크][build-essential]입니다.
```
apt-get install build-essential
```
해당 패키지가 설치되고 나서 다시 `apt-get install jekyll`명령어를 사용하시면 잘 작동하시는 것을 보실 수 있습니다. 

이후 bundler를 설치 해줍니다.
```
apt-get install bundler 
bundle install
```
이때 nokogiri가 설치되지 않는 문제가 발생 할 수 있습니다. 
이때도 의존성 소프트웨어가 설치 되있지 않아서 생기는 문제입니다.
이 문제를 해결하기위해서는 해당 명령어를 이용하여 의존 패키지를 설치해줍니다.
참고한 [링크][nokogiri]입니다.
```
apt-get install patch ruby-dev zlib1g-dev liblzma-dev
```
설치가 된 이후 다시 `bundle install`명령어를 이용하여 설치를 진행해주시면 됩니다.

이후 과정이 오류없이 설치가 완료된다면 `bundle exec jekyll serve`명령어를 이용하여 github-page를 실행할 수 있습니다 
오류 없이 실행이 된다면 `http://localhost:4000/`으로 접속하시면 자신이 폴더내에서 수정한 블로그를 확인 할 수 있습니다.  
수정이 끝난 후에는 git push를 통해 업로드 하시면 적용가능합니다!

해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~
같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[nokogiri]:https://nokogiri.org/tutorials/installing_nokogiri.html
[build-essential]:https://github.com/sj26/mailcatcher/issues/144#issuecomment-48008579