---
layout: post
title: "[Python] 프로그래머스, 네트워크, DFS, Algorithm"
date:   2018-10-07 20:00:00 +0300
description: 파이썬에서 프로그머스 네트워크 문제 DFS 알고리즘으로 해결 # Add post description (optional)
img: python.jpg # Add image post (optional)
categories: IT
tags: [Blog, IT, Language, Python, Algorithm]
author: Jiho # Add name author (optional)
---
안녕하세요! **Do My Best 블로그** 세번째 게시물입니다. ㅎㅎ  
이번에는 프로그래머스의 알고리즘 문제 중 LEVEL 3 네트워크 문제를 DFS알고리즘으로 해결해보겠습니다. 

**DFS는 Depth First Search**로 깊이 우선 탐색입니다.

DFS알고리즘은 검색을 통해 자세히 나와있으니 참고 하시면 되겠습니다!  
여기서는 간단하게 DFS알고리즘에대해서 설명하고 넘어가겠습니다.   
DFS알고리즘은 자식의 자식 끝까지 먼저 탐색합니다.! 너무 간단한가요??

먼저 프로그래머스의 네트워크 문제는 올라온지 얼마 안되서 그런지 문제 푼 분들이 많이 없네요?  
무려!! **29명!**  

![programmers_network]({{site.baseurl}}/assets/img/programmers_network.png)

참고하면서 문제를 한번 풀어보겠습니다.

{% highlight ruby %}
def solution(n, computers):
    answer = 0
    visited = [0 for i in range(n)]
    def dfs(computers, visited, start):
        stack = [start]
        while stack:
            j = stack.pop()
            if visited[j] == 0:
                visited[j] = 1
            for i in range(len(computers)):
                #pop한 정점과 연결되어있고 방문하지 않은곳 stack에 저장
                if computers[j][i] ==1 and visited[i] == 0:
                    #stack에 저장하고나면 해당정점과 다시 pop하면서 정점과 연결된 곳을 모두 방문함
                    stack.append(i)
    i=0
    while 0 in visited:
        if visited[i] ==0:
            dfs(computers, visited, i)
            answer +=1
        i+=1
    return answer
{% endhighlight %}


지금까지 DFS 알고리즘을 이용한 프로그래머스 LEVEL 3문제인 **네트워크 풀이**였습니다.   
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^
