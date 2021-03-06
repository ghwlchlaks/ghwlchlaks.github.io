---
layout: post
title: "순열과 조합 라이브러리를 사용해보자 [Python] "
date:   2018-10-06 00:00:00 
description: 파이썬에서 순열과 조합 경우의 수 출력. # Add post description (optional)
categories: Jiho
tags: [Blog, IT, Language, Python]
navigation: True
subclass: 'post tag-IT tag-Language tag-Python'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/python.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 첫 게시물입니다. ㅎㅎ  
언제부터 올려야할지 뭐부터 올려야할지 고민이되서 그냥 '일단 아무거나 올려보자!'란 마음먹고 올리게되었습니다.  
ㅎㅎ 일단 해보는게 중요하겠죠?

이번에 포스팅할거는요~ 파이썬 언어에서 라이브러리를 이용한 순열과 조합입니다.   
경우의 수는 쉽게 구하지만 모든 경우의 수는 알고리즘을 통해 구현하거나, 밑에 방법처럼 라이브러리를 이용해야겠죠? 

우선 순열 라이브러리 사용방법에대해서 간단하게 설명하도록 하겠습니다.!

순열을 `nPr`로 표현하는데요~ n개중에 r개를 뽑아 나열하는 경우의 수입니다.  

**#순열 : 중복 허용x**
`permutations` 중복을 허용하지 않습니다.  
{% highlight ruby %}
from itertools import permutations
per = permutations(["빨","주","노","초"],2)
print(list(per))
#=> [('빨', '주'), ('빨', '노'), ('빨', '초'), ('주', '빨'), ('주', '노'), ('주', '초'), ('노', '빨'), ('노', '주'), ('노', '초'), ('초', '빨'), ('초', '주'), ('초', '노')]
{% endhighlight %}

**#순열 : 중복 허용o**  
`product`는 중복을 허용한 방법입니다. 이때 `repeat`으로 인자를 설정해야합니다!  
{% highlight ruby %}
from itertools import product
per1 = product((["빨","주","노","초"]), repeat=2)
print(list(per1))
#=> [('빨', '빨'), ('빨', '주'), ('빨', '노'), ('빨', '초'), ('주', '빨'), ('주', '주'), ('주', '노'), ('주', '초'), ('노', '빨'), ('노', '주'), ('노', '노'), ('노', '초'), ('초', '빨'), ('초', '주'), ('초', '노'), ('초', '초')]
{% endhighlight %}

조합은 `nCr`로 표현하는데요~ n개중에 r개를 뽑는 수 입니다.  
나열하는 경우가 없는 것에서 순열과 차이가 있죠?  

**#조합 : 중복 허용x**
`combinations`는 중복을 허용하지 않습니다.  
{% highlight ruby %}
from itertools import combinations
print(list(combinations('빨주노초',2)))
#=> [('빨', '주'), ('빨', '노'), ('빨', '초'), ('주', '노'), ('주', '초'), ('노', '초')]
{% endhighlight %}

**#조합 : 중복 허용o**
`combinations_with_replacement`는 중복을 허용한 방법입니다.  
{% highlight ruby %}
from itertools import combinations_with_replacement
print(list(combinations_with_replacement("빨주노초",2)))
#=> [('빨', '빨'), ('빨', '주'), ('빨', '노'), ('빨', '초'), ('주', '주'), ('주', '노'), ('주', '초'), ('노', '노'), ('노', '초'), ('초', '초')]
{% endhighlight %}

결과값을 확인해보시고 차이점을 생각해보세요~

지금까지 파이썬 라이브러리를 이용하여 순열과 조합 모든 경우의 수 계산 방법이었습니다.   
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`