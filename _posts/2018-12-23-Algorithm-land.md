---
layout: post
title: "[프로그래머스 LEVEL2] 땅 따먹기 [파이썬]"
date:   2018-12-23 00:00:00
description: 땅 따먹기 [파이썬] # Add post description (optional)
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

이번에 포스팅할 내용은  **프로그래머스 문제 LEVEL2에 해당되는 땅 따먹기 문제**를 풀어보도록 하겠습니다.

해당 문제는 [프로그래머스 웹페이지][programmers-land]에서 만나보실 수 있습니다.

# 문제
땅은 총 N행 4열로 이루어져있습니다. 1행부터 땅을 밟으며 한 행씩 내려옵니다. 각 행은 한칸씩 밝아야하며, 같은 열을 연속해서 밟을 수는 없습니다. 이때 마지막행에서 최고 점을 받는 점수를 리턴하시오.

입출력 예제는 [프로그래머스 웹페이지][programmers-land]에서 확인하세요!

**제한 사항**
>* 행의 개수 N: 100,000 이하의 자연수 
>* 열의 개수 4, 땅은 2차원 배열
>* 점수 : 100이하의 자연수

해당 문제는 **dp(다이나믹 프로그래밍)**에 대표적인 문제이기도 합니다.
dp를 풀면서 해당 문제를 풀어보도록 하겠습니다. 

# 풀이
{% highlight ruby %}
    for i in range(len(land)-1):
        land[i+1][0] = max(land[i][1], land[i][2], land[i][3]) + land[i+1][0]
        land[i+1][1] = max(land[i][0], land[i][2], land[i][3]) + land[i+1][1]
        land[i+1][2] = max(land[i][0], land[i][1], land[i][3]) + land[i+1][2]
        land[i+1][3] = max(land[i][0], land[i][1], land[i][2]) + land[i+1][3]
    
    return max(land[-1])
{% endhighlight %}  

i+1번째행에 최댓값은 이전 행에 최댓값을 더한겁니다.   
또한 자기 자신에 열을 연속해서 밟으면 안되므로 자신을 제외한 열의 max값을 구합니다.   
즉 하나의 행열에서의 최댓값을 구하는 식은 `land[i+1][0] = max(land[i][1], land[i][2], land[i][3]) + land[i+1][0]`  입니다.   
그러면 마지막 행에는 모든 경로의 최댓값이 들어가게됩니다.   
마지막행에서 최댓값을 구하면 위에 조건을 만족하면서 최대점수를 구할 수 있습니다.

다이나믹 프로그래밍은 아직 너무 어렵네요.. ㅠㅠ 좀 더 공부하도록 하겠습니다.!

지금까지 **프로그래머스 문제 LEVEL2에 해당되는 땅 따먹기 문제**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[programmers-land]:https://programmers.co.kr/learn/courses/30/lessons/12913