---
layout: post
title: "일반적으로 .gitignore에 등록하는 파일 [Git]"
date:   2018-12-13 00:00:00
description: 일반적으로 .gitignore에 등록하는 파일 [Git] # Add post description (optional)
img: github.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Git]
navigation: True
subclass: 'post tag-IT tag-Git'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/github.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다.    

이번에는 **일반적으로 .gitignore에 등록하는 파일**에 대해서 포스팅하겠습니다. 

.gitignore는 git에 올리지 말아야하거나 올릴 필요가 없는 파일을 미리 등록하여 git add를 통해 staging영역에 올라가지 않는 파일을 설정한 파일을 말합니다.
파일 명은 `.gitignore`입니다.

이때 일반적으로 올리지 않는 형식에대해서 다뤄보고자 합니다. 

**순서**
>1. 실행파일 제외
>2. 로그파일 제외
>3. 문서 파일 제외
>4. 패키지 파일 제외
>5. OS용 시스템 파일 제외
>6. 자신의 에디터[Eclipse, VSCode] 설정 파일 제외

**1. 실행파일 제외**  
{% highlight ruby %}
*.dll
*.exe
*.o
*.so
*.com
*.class
#=> 컴파일된 결과물입니다. 올릴 이유가 없겠죠?
#=> *은 모두들 아시다시피 전체를 뜻하는 별칭입니다. 앞으로 많이 사용됩니다~
{% endhighlight %}


**2. 로그파일 제외**  
{% highlight ruby %}
*.log
logs/
#=> 로그파일은 개발자마다 다르니 올릴 이유가 없겠죠?
#=> 폴더를 등록할경우 위에처럼 logs/ 선언하면됩니다. 그러면 logs폴더 내부에 모든 파일이 제외 대상입니다.
{% endhighlight %}

**3. 문서 파일 제외**  
{% highlight ruby %}
*.xlsx
*.xls
*.pdf
*.docs
*.ppt
*.pptx
#=> 문서형식은 올리지 않도록 설정합니다. 위에 형식이 자주 사용하는 파일 형식이죠?
#=> 물론 필요에 따라서 문서를 올리기도 합니다 그때는 적절히 .gitignore파일을 수정해주면 되겠죠?
{% endhighlight %}

**4. 패키지 파일 제외**  
{% highlight ruby %}
*.dmg
*.iso
*.tar
*.zip
*.gz
#=> 압축파일 형식입니다. 
{% endhighlight %}


**5. OS용 시스템 파일 제외**  
{% highlight ruby %}
.Trashes
.Thumbs.db
.ehthumbs.db
#=> 개발때 사용한 운영체제별 시스템 파일은 제외해야겠죠?
{% endhighlight %}

**6. 자신의 에디터[Eclipse, VSCode] 설정 파일 제외**  
{% highlight ruby %}
#=> Eclipse
.metadata
bin/
tmp/
*.tmp
*.bak
*.swp
local.properties
.settings/
.loadpath
.recommenders
.project
.externalToolBuilders/
*.launch
.classpath
.factorypath
.buildpath
.target
.springBeans
.recommenders/
-----------------------------------------------------------------------------
#=> VSCode
.vscode/*
!.vscode/settings.json
!.vscode/tasks.json
!.vscode/launch.json
!.vscode/extensions.json
#=> 이클립스를 사용하면 생성되는 설정 파일 혹은 임시 파일들은 제외합니다. 
#=> 해당 정보는 개발자마다 PC환경이 다르기 때문에 설정 정보를 넣어서 push하게 된다면
#=> 해당 내용을 받는 개발자들에 이클립스 환경에 덮어쓰기가되어 동작하지않는 이슈가 생길 수 있습니다. 
#=> 이클립스 뿐만아니라 다른 에디터를 사용하면서 생기는 설정, 임시 파일을 제외해주세요~
{% endhighlight %}

해당 내용 이외에도 제외하고자하는 파일 형식이나 폴더를 등록해주시면 git 저장소에 쓸데없는 내용이 업로드 되지 않겠죠?ㅎㅎ   

여기까지 `일반적으로 .gitignore에 등록하는 파일`에대해서 포스팅했습니다.   

   
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 
같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  
