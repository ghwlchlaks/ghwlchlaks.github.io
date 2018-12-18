---
layout: post
title: "[프로그래머스 LEVEL1] 완주하지 못한 선수 프로그래머스 해시 [파이썬]"
date:   2018-12-18 12:00:00
description: 완주하지 못한 선수 프로그래머스 해시 [파이썬] # Add post description (optional)
img: python.jpg # Add image post (optional)
categories: JIho
navigation: True
subclass: 'post tag-IT tag-Language tag-Python tag-Algorithm'
tags: [Blog, IT, Language, Python, Algorithm]
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/python.jpg'
author: Jiho # Add name author (optional)
disqus: true
---

안녕하세요! **Do My Best 블로그**입니다. ㅎㅎ  

이번에 포스팅할 내용은 스택/큐에 해당되는 **프로그래머스 문제 LEVEL1에 해당되는 완주하지 못한 선수 알고리즘 문제**를 풀어보도록 하겠습니다.

오랜만에 알고리즘 문제를 풀어보도록 하겠습니다 ㅎㅎ  

해당 문제는 [프로그래머스 웹페이지][programmers-finalplayer]에서 만나보실 수 있습니다.

# 문제
마라톤에 참여한 선수들의 이름이 담긴 배열과 완주한 선수들의 이름이 담긴배열이 주어질 때, 완주하지 못한 선수의 이름을 return하는 문제입니다. 

입출력 예제는 [프로그래머스 웹페이지][programmers-finalplayer]에서 확인하세요!

**제한 사항**
>* 참여 선수의 수는 1명 이상 100,000명 이하입니다. 
>* 마라톤에 참여한 배열의 길이는 완주한 선수들의 배열보다 큽니다.
>* 참가자의 이름은 1개이상 20개이하의 알파벳 소문자로 이루어져있습니다.
>* 참가자 중에는 동명이인이 있을수 있습니다.
  
# 풀이
{% highlight ruby %}
import collections
def solution(participant, completion):
    return list((collections.Counter(participant) -collections.Counter(completion)).keys())[0]
{% endhighlight %}   

해당 문제는 collections를 이용하여 해결하였습니다.   
collections.Counter(list) 메소드는 리스트를 dictionary 형태로 숫자를 세서 반환합니다. 

예를들어 
{% highlight ruby %}
import collections
list = ["a", "b", "c" ,"a"]
collections.Counter(list)
{% endhighlight %}   
일때 결과 값은 `{a:2, b: 1, c:1}`입니다.
해당 형태로 다른 딕셔너리 형태와 사칙연산을 할 수 있습니다. 

즉 참가자 중에 동명이인이 있으므로 collections.Counter() 메소드를 이용하여 참가자 수와 완주한 사람의 수를 딕셔너리 형태로 얻은 후 남은 값들은 완주하지 못한 사람이 됩니다.
해당 값에서 key를 출력하면 간단히 문제를 해결 할 수 있습니다.

지금까지 **완주하지 못한 선수 프로그래머스 해시 [파이썬]**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[programmers-finalplayer]:https://programmers.co.kr/learn/courses/30/lessons/42576