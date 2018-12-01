---
layout: post
title: "Jekyll custom plugin (로컬은되는데 원격은 안될때) [Jekyll]"
date:   2018-12-01 00:00:00
description: jekyll 커스텀 플러그인 사용방법 (로컬은 되는데 원격은 안될때) [Jekyll] # Add post description (optional)
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
안녕하세요! **Do My Best 블로그** 입니다.  
오래만에 포스팅합니다.ㅠㅠ 요즘 다른일에 집중하느라.. (핑계..)   

이번에는 제가 Jekyll theme에 기능들을 수정하다가 생긴 이슈에 대해서 생긴 이슈를 해결하는 방법에대해서 설명드리도록 하겠습니다.  

jekyll plugin에서 custom plugin을 보실수 있습니다. 그런데 여러가지 기능을 추가하다보면 local상에서는 정상 작동되는데 github에 업로드하여 사이트에 접속했을때는 404 에러 혹은 문제가 발생할 수 있습니다. (경로문제가 아닐때 ㅎㅎ)    

해당 이슈를 해결하는 방법에대해서 포스팅 하겠습니다.   

해당 이슈가 생기는 이유는 github에서 보안 문제로 custom plugin이 적용이되지 않는다고 하네요 ㅎㅎ  

**해결 순서**
>1. local repository상에서 master브랜치에서 분기한 다른 브랜치를 생성  (여기서는 source 브랜치 생성)
>2. local repository와 remote repository에서 master브랜치 삭제
>3. source브랜치에서 .gitignore파일 _site폴더 주석 혹은 삭제 처리
>4. source브랜치에서 .nojekyll 파일 생성 및 _config.yml 파일 수정
>5. source브랜치에서 _site폴더만 필터링 해서 master브랜치 생성
>6. master브랜치와 source브랜치 전체 push 하기
>7. 웹사이트 정상 작동 확인
>8. 해당 순서를 shell script를 만들어서 간편화 하기

해당 순서만 보고 따라해도 되겠지만 왜 저렇게 하는지 가볍게 알고 넘어가는게 좋겠죠?
우선 github 블로그는 master브랜치만 적용이되어 블로그가 생성 및 갱신됩니다.   
그래서 master브랜치에 아예 local에서 정상 작동되는 _site폴더를 master브랜치에 push하여 해결하는 방식입니다.   
여기서 _site폴더는 local에서 jekyll build를 할때 갱신되는 것은 알고 계실것이라고 생각합니다.   
그리고 source브랜치는 _post및 전체 블로그의 소스를 관리하는 브랜치입니다.  
여기서 갱신및 추가한 소스를 jekyll build하여 _site폴더가 갱신되면
해당 _site를 필터링하여 master브랜치에 업로드하는 방식입니다.   

그럼 해결 순서대로 시작해보겠습니다. 

**1. local repository상에서 master브랜치에서 분기한 다른 브랜치를 생성(여기서는 source 브랜치 생성)**  
{% highlight ruby %}
git checkout -b source
=> source 브랜치를 생성하고 해당 브랜치로 이동
{% endhighlight %}

**2. local repository와 remote repository에서 master브랜치 삭제**  
{% highlight ruby %}
git push origin :master
=> remote repository에 master브랜치 삭제
git branch -D master
=> local repository에서 master브랜치 삭제
{% endhighlight %}

**3. source브랜치에서 .gitignore파일 _site폴더 주석 혹은 삭제 처리**  
기본적으로 _site폴더는 .gitignore에서 업로드 못하게 되어있습니다. 
이 주석을 제거해줍시다!

**4. source브랜치에서 .nojekyll 파일 생성 및 _config.yml 파일 수정**  
.nojekyll 파일을 생성
_config.yml파일 수정
{% highlight ruby %}
include:  
  \- .nojekyll
=> 해당 코드를 추가해 줍니다!
{% endhighlight %}

**5. source브랜치에서 _site폴더만 필터링 해서 master브랜치 생성**  
{% highlight ruby %}
git filter-branch --subdirectory-filter _site -f HEAD
=> 현재 HEAD에서 _site 폴더를 필터링하는 명령어 입니다. git에서 제공하고요~
{% endhighlight %}

**6. master브랜치와 source브랜치 전체 push 하기**  
{% highlight ruby %}
git push --all 
=> 전체 branch를 push 하는 명령어입니다.
{% endhighlight %}

**7. 웹사이트 정상 작동 확인**  
업로드 후 자신의 사이트에서 정상 작동하는지 확인하시면 됩니다.
기본적으로 github 브랜치 구조는 다음과 같습니다. 

master branch (source 브랜치에서 build된 _site폴더내부)  
<img src="/assets/images/2018-12-01-Jekyll-custom-plugin/master.PNG">

source branch (소스를 관리하는 전체 소스)  
<img src="/assets/images/2018-12-01-Jekyll-custom-plugin/source.PNG">

**8. 해당 순서를 shell script를 만들어서 간편화 하기**  
매번 위와 같이 반복작업을 하다보면 매우 귀찮겠죠? 이것을 한번에 처리하기 위해 
shell script를 만들어 보겠습니다 파일명.sh을 만든 후 해당 코드를 입력합니다.  
{% highlight ruby %}
#!/bin/bash
git checkout source
=> source 브랜치로 이동 
git branch -D master
=> 병합되지 않은 master 브랜치 삭제
git checkout -b master
=> master브랜치 생성 (당연히 souce브랜치에서 build후 git add, git commit을 한 이후여야겠죠?)
git filter-branch --subdirectory-filter _site -f HEAD
=> 브랜치 필터링을 통해 _site 추출
git push --all
=> master, source 브랜치 모두 github에 push
git checkout source
=> 다시 소스를 관리하는 source 브랜치로 이동
{% endhighlight %}
이렇게 shell script를 만든 후 윈도우는 환경변수 설정을 해주시면 되는데요   
저는 에디터에서 파일경로 복사하고 에디터 터미널에 붙여넣기 하는 방식으로 합니다.   
편하신 방법으로 하시면 되겠습니다.  

물론 당연한거지만 `주의하실점`은 source브랜치에서 bundle exec jekyll build or bundle exec jekyll serve 명령어로 build하신 후 (local에서 확인 하실 꺼니깐 당연히 하실꺼라 생각합니다.) git add, git commit을 하셔야합니다.   
그래야 _site폴더가 갱신된 상태에서 local repository에 적용이 되니깐요 ㅎㅎ  
그 후 쉘스크립트 또는 위에 순서대로 진행하시면 됩니다.    

해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~
같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  
