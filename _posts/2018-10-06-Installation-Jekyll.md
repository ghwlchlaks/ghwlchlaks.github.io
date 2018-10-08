---
layout: post
title: "윈도우에서 지킬 설치 및 실행 [Jekyll]"
date:   2018-10-06 01:00:00 +0300
description: 윈도우에서 지킬 설치 및 실행. # Add post description (optional)
img: github.png # Add image post (optional)
categories: IT
tags: [Blog, IT, Github, Jekyll]
author: Jiho # Add name author (optional)
---
안녕하세요! **Do My Best 블로그** 두번째 게시물입니다. ㅎㅎ  
지킬 사용하다가 이것도 게시하면 다른 분들에게 많은 도움이 될 것 같아서 첫번째 게시물 이후에 바로 올립니다.!

이번에 포스팅할거는요~ Jekyll을 사용하여 github에 수정한 블로그 내용은 push하고 확인하는 것이 아니라 로컬에서 작업한 내용을 확인 하는 방법에대해서 포스팅하려고합니다.!

**1. 루비 (Ruby) 설치!**  
우선 루비를 설치해야합니다.!  
저도 루비 설치 안해서.. 계속 안됐다는.. 하하.. 
[루비 설치 링크][루비-설치-링크] 입니다.  
이곳에 접속하셔서 윈도우용루비 + 개발자킷(DevKit)설치 프로그램을 다운로드 하시면됩니다.  
과정중에 PATH설정도 해주는 checkbox를 체크 해주세요~~ 자동으로 PATH를 잡아줍니다~ 용량이 좀 되네요...?ㅎㅎ 

**2. 지킬 (Jekyll) 설치**  
Ruby Command prompt창을 시작합니다.  
윈도우 검색창에서 검색하시면 바로 나옵니다~ 콘솔창이 켜지면 gem명령어를 이용하여 설치를 진행합니다.! 시간이 좀걸려요~

{% highlight ruby %}
gem install jekyll
gem install minima
gem install bundler
gem install jekyll-feed
gem install tzinfo-data
{% endhighlight %}  
설치가 오류 없이 정상적으로 설치되면 다음으로~  
오류가 생긴다면 추가적으로 필요한 모듈이 로그에 나오니깐 추가적으로 설치하시면 되요~  

**3. 로컬에서 블로그 실행**  
우선 로컬에 자신의 블로그 git폴더가 있어야겠죠?  
그 후 폴더 내에서 `jekyll serve`를 이용하여 실행 합니다.  
{% highlight ruby %}
#자신의 블로그 복제하여 다운로드
git clone https://github.com/username.git.io/
#폴더내로 이동
cd username.git.io
#로컬에서 블로그 실행! 요것은 ruby prompt에서 실행해야겠죠?
jekyll serve
{% endhighlight %}

오류 없이 실행이 된다면 `http://localhost:4000/`으로 접속하시면 자신이 폴더내에서 수정한 블로그를 확인 할 수 있습니다.  
수정이 끝난 후에는 git push를 통해 업로드 하시면 적용가능합니다!

해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~
같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[루비-설치-링크]: https://rubyinstaller.org/downloads/