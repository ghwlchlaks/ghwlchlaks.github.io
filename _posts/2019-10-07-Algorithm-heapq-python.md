---
layout: post
title: "[Python] 프로그래머스, 이중우선순위큐, 라이브러리, Algorithm"
date:   2018-10-07 20:30:00 +0300
description: 파이썬에서 프로그머스 이중우선순위큐 heapq라이브러리로 해결 # Add post description (optional)
img: python.jpg # Add image post (optional)
categories: IT
tags: [Blog, IT, Language, Python, Algorithm]
author: Jiho # Add name author (optional)
---
안녕하세요! **Do My Best 블로그** 네번째 게시물입니다. ㅎㅎ  
이번에는 프로그래머스의 알고리즘 문제 중 LEVEL 3 이중우선순위큐 문제를 **heapq 라이브러리**를 이용하여 해결해보겠습니다. 

**heapq**는 
완전 이진 트리의 일종으로 우선순위 큐를 위하여 만들어진 자료구조입니다.  
여러 개의 값들 중에서 최댓값이나 최솟값을 일반적인 queue보다 빠르게 찾아내도록 만들어진 자료구조입니다.

**heapq라이브러리** 사용방법에 대해서도 후에 포스팅 하겠습니다.

이 문제 또한 프로그래머스 문제인데요. 이것 또한 푼 사람이 아직 별로 없네요~~  
문제 자체는 어렵지 않은것 같아요~ 얼마나 효율적이게 해결하냐는 문제같은데 저도 좀 더 봐야겠어요~

{% highlight ruby %}
def solution(operations):
    import heapq
    answer = []
    priority_queue = []
    
    for operation in operations:
        op, num = operation.split()
        #insert
        if op == "I":
            heapq.heappush(priority_queue, int(num))
        #delete 
        elif op == "D" and priority_queue:
            #max data delete
            if num == "1":
                data = max(priority_queue)
                priority_queue.pop(priority_queue.index(data))
            #min data delete
            elif num == "-1":
                heapq.heappop(priority_queue)
    if priority_queue:
        #max
        answer.append(max(priority_queue))
        #min
        answer.append(heapq.heappop(priority_queue))
    else:
        answer = [0,0]
    return answer
{% endhighlight %}

저는 이렇게 풀었는데요... 시간초과 걸릴것같아서 heaq를 사용했는데 
다른 분들이 적은 답을보니 heapq사용하지 않고 배열에 넣고 min max 값을 찾아도 시간초과가 
나지 않는 것같습니다.  
여러가지 방법으로 풀어보세요~

지금까지 파이썬의 heapq 라이브러리를 이용한 프로그래머스 LEVEL 3문제인 **이중우선순위큐  풀이**였습니다.   
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^
