---
layout: post
title: "[프로그래머스 LEVEL2] 더맵게 프로그래머스 heap [파이썬]"
date:   2018-10-20 12:00:00
description:  더맵게 프로그래머스 heap [파이썬] 프로그래머스 LEVEL2 # Add post description (optional)
img: python.jpg # Add image post (optional)
categories: IT
navigation: True
subclass: 'post tag-IT tag-Language tag-Python tag-Algorithm'
tags: [Blog, IT, Language, Python, Algorithm]
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/python.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그**입니다. ㅎㅎ  

이번에 포스팅할 내용은 힙(Heap)과 관련된 **프로그래머스 문제 LEVEL2에 해당되는 더맵게 알고리즘 문제**를 풀어보도록 하겠습니다.

해당 문제는 [프로그래머스 웹페이지][programmers-morespicy]에서 만나보실 수 있습니다.

# 문제
매운 것을 좋아하는 Leo는 모든 음식의 스코빌 지수를 K 이상으로 만들고 싶습니다.  
 모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 Leo는 스코빌 지수가 가장 낮은 두 개의 음식을 아래와 같이 특별한 방법으로 섞어 새로운 음식을 만듭니다.
>섞은 음식의 스코빌 지수 = 가장 맵지 않은 음식의 스코빌 지수 + (두 번째로 맵지 않은 음식의 스코빌 지수 * 2)

**제한 사항**
>* scoville의 길이는 1 이상 1,000,000 이하입니다.
>* K는 0 이상 1,000,000,000 이하입니다.
>* scoville의 원소는 각각 0 이상 1,000,000 이하입니다.
>* 모든 음식의 스코빌 지수를 K 이상으로 만들 수 없는 경우에는 -1을 return 합니다.
  
# 풀이
{% highlight ruby %}  
def solution(scoville, K):
    import heapq
    data = []
    for s in scoville:
        heapq.heappush(data, s)
    answer = 0
    while len(data) >0:
        if data[0] >= K:
            return answer
        a= heapq.heappop(data)
        if data != []:
            b =heapq.heappop(data)
            heapq.heappush(data,a + (b *2))
        answer +=1    
    return -1
{% endhighlight %}   

해당 문제는 heapq 모듈을 import하여 해결하였습니다.  
heapq를 사용하지 않고 일반 배열에서 queue나 stack방식을 사용한다면 시간초과가 발생하네요.. ㅠㅠ  
heapq에대한 설명은 [heapq를 사용해보자 [Python]][mysite-2018-10-08-Heapq-Python] 에서 볼 수 있습니다.   
또한 heapq를 사용하여 다른 알고리즘 문제를 해결한 것은 [이중우선순위큐 알고리즘 [Python]][mysite-2018-10-07-Algorithm-Heapq-Python]에서 볼 수 있습니다.

지금까지 **더맵게 프로그래머스 heap [파이썬]**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[programmers-morespicy]:https://programmers.co.kr/learn/courses/30/lessons/42626
[mysite-2018-10-08-Heapq-Python]:https://ghwlchlaks.github.io/Heapq-Python/
[mysite-2018-10-07-Algorithm-Heapq-Python]:https://ghwlchlaks.github.io/Algorithm-Heapq-Python/