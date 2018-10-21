---
layout: post
title: "[프로그래머스 LEVEL2] 탑 프로그래머스 스택/큐 [파이썬]"
date:   2018-10-18 12:00:00
description:  탑 프로그래머스 스택/큐 [파이썬] 프로그래머스 LEVEL2 # Add post description (optional)
img: python.jpg # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Language, Python, Algorithm]
navigation: True
subclass: 'post tag-IT tag-Language tag-Python tag-Algorithm'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/python.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그**입니다. ㅎㅎ  

이번에 포스팅할 내용은 스택/큐에 해당되는 **프로그래머스 문제 LEVEL2에 해당되는 탑 알고리즘 문제**를 풀어보도록 하겠습니다.
오랜만에 알고리즘 문제를 풀어보겠습니다!

해당 문제는 [프로그래머스 웹페이지][programmers-top]에서 만나보실 수 있습니다.  

# 문제
수평 직선에 높이가 서로 다른 탑 N대를 세웠습니다. 모든 탑의 꼭대기에는 신호를 송/수신하는 장치를 설치했습니다. 발사한 신호는 신호를 보낸 탑보다 높은 탑에서만 수신합니다. 또한, 한 번 수신된 신호는 다른 탑으로 송신되지 않습니다.

높이가 6, 9, 5, 7, 4인 다섯 탑이 왼쪽으로 동시에 레이저 신호를 발사합니다. 그러면, 탑은 다음과 같이 신호를 주고받습니다. 높이가 4인 다섯 번째 탑에서 발사한 신호는 높이가 7인 네 번째 탑이 수신하고, 높이가 7인 네 번째 탑의 신호는 높이가 9인 두 번째 탑이, 높이가 5인 세 번째 탑의 신호도 높이가 9인 두 번째 탑이 수신합니다. 높이가 9인 두 번째 탑과 높이가 6인 첫 번째 탑이 보낸 레이저 신호는 어떤 탑에서도 수신할 수 없습니다.

**제한 사항**
* heights는 길이 2 이상 100 이하인 정수 배열입니다.
* 모든 탑의 높이는 1 이상 100 이하입니다.
* 신호를 수신하는 탑이 없으면 0으로 표시합니다.
  
# 풀이
{% highlight ruby %}
def solution(heights):
    answer = [0] * len(heights)
    while heights:
        right = heights.pop()
        for idx in range(len(heights)-1,-1,-1):
            if heights[idx] > right:
                answer[len(heights)] = idx+1
                break
    return answer
{% endhighlight %}   

풀이 방법은 heights 배열에 오른쪽 부터 pop()을 한 후 pop()한 value와 남은 height의 원소들은 거꾸로 비교하여 큰 수가 나오면 해당 인덱스를 저장하는 방식입니다.  
마지막 원소를 pop()한다는 것에서 스택과 연관되어 풀수 있었네요 ㅎㅎ

지금까지 **탑 프로그래머스 스택/큐 [파이썬]**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[programmers-top]:https://programmers.co.kr/learn/courses/30/lessons/42588