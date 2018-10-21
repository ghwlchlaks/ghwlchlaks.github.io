---
layout: post
title: "heapq를 사용해보자 [Python] "
date:   2018-10-08 03:10:00
description: 파이썬에서 heapq 라이브러리 # Add post description (optional)
img: python.jpg # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Language, Python]
navigation: True
subclass: 'post tag-IT tag-Language tag-Python'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/python.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 다섯번째 게시물입니다. ㅎㅎ  
이번에는 세번째 게시물에서 포스팅 예정한 **heapq 라이브러리** 사용방법 입니다.

힙(heap)은 최댓값 및 최솟값을 찾아내는 연산을 빠르게 하기 위해 고안된 완전이진트리(Complete binary tree)를 기본으로 한 자료구조(tree-based structure)로서 다음과 같은 힙 속성(property)을 만족합니다!  
A가 B의 부모노드(parent node) 이면, A의 키(key)값과 B의 키값 사이에는 대소관계가 성립합니다!

예제를 보면서 **heapq 라이브러리** 사용방법에 대해 배워요!

사용방법은 매우 간단합니다. 파이썬에서 일반 배열을 사용할 줄 아시면 됩니다.!

**heapq 만드는 2가지 방법**  
{% highlight ruby %}
#1
import heapq
data = []
heapq.heapush(data,1)
heapq.heappush(data, -1)
heapq.heappush(data, 2)
heapq.heappush(data, -6)
heapq.heappush(data, 7)
heapq.heappush(data, 8)
print(data)
#=> [-6, -1, 2, 1, 7, 8] 
{% endhighlight %}

{% highlight ruby %}
#2
a = [1,-1,2,-6,7,8]
heapq.heapify(a)
print(a)
#=> [-6, -1, 2, 1, 7, 8] 
{% endhighlight %}

**우선순위순으로 출력**
우선순위는 작을 수록 높습니다.!   
{% highlight ruby %}
print(heapq.heappop(data))
print(data)
#=> -6
#=> [-1, 1, 2, 8, 7]
{% endhighlight %}
우선순위가 낮은걸 pop하고 싶을때는 -1을 곱하는 방법으로도 가능하겠네요 ㅎ

간단한 예제가 끝났습니다.! 이제~ 결과값을 보고 생각해보아요~   
[파이썬 heapq 라이브러리][파이썬-heapq-라이브러리]입니다. 참고하시면 좋을것같아요~

지금까지 파이썬 라이브러리인 **heapq** 사용방법이었습니다.   
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[파이썬-heapq-라이브러리]: https://docs.python.org/3.0/library/heapq.html