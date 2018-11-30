---
layout: post
title: "[프로그래머스 LEVEL2] 주식가격 프로그래머스 [파이썬]"
date:   2018-10-21 12:00:00
description:  주식가격 프로그래머스 스택/큐 [파이썬] 프로그래머스 LEVEL2 # Add post description (optional)
img: python.jpg # Add image post (optional)
categories: Jiho
navigation: True
subclass: 'post tag-IT tag-Language tag-Python tag-Algorithm'
tags: [Blog, IT, Language, Python, Algorithm]
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/python.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그**입니다. ㅎㅎ  

이번에 포스팅할 내용은 스택(stack)/큐(queue)와 관련된 **프로그래머스 문제 LEVEL2에 해당되는 주식가격 알고리즘 문제**를 풀어보도록 하겠습니다.

해당 문제는 [프로그래머스 웹페이지][programmers-stockprice]에서 만나보실 수 있습니다.

# 문제
초 단위로 기록된 주식가격이 담긴 배열 prices가 매개변수로 주어질 때, 가격이 유지된 기간은 몇 초인지를 계산하는 문제입니다.

**제한 사항**
>* prices의 각 가격은 1 이상 10,000 이하인 자연수입니다.
>* prices의 길이는 2 이상 100,000 이하입니다.
  
# 풀이
{% highlight ruby %}  
def solution(prices):
    answer = [0] * len(prices)

    for i in range(len(prices)-1):
        for j in range(i, len(prices)-1):
            if prices[i] >prices[j]:
                break
            else:
                answer[i] +=1
    return answer
{% endhighlight %}   

해당 문제는 스택/큐 부분이지만 이중 for문을 이용해서 풀었습니다.  
다른 분들이 푸신내용보니깐 큐를 이용해서 (pop(0)) 푸시는 분들도 많았습니다.  
사실 저도 큐를 이용하여 접근하였지만 시간초과가 발생해서 간단히 이중for문을 이용했습니다.  
시간의 큰차이는 없어보였는데 시간 제한사항이 역시나 민감하네요 
ㅎㅎ 처음에 시간초과가 발생해서 살짝 당황했습니다. ㅎㅎ

# 풀이방법
처음 i 변수를 가지는 for문은 비교할 기준의 요소를 정하는 인덱스입니다.  
안에 j 변수를 가지는 for문은 인덱스 i부터 끝까지 비교할 대상의 인덱스를 나타냅니다.  
안에 `if prices[i] > prices[j]`는 기준에 비해 가격이 유지되지 않고 떨어지는 인덱스를 가졌을때 해당 for문을 벗어나는 코드입니다.  
`else`부분은 이외에는 count를 1씩 증가시켜줍니다. 

지금까지 **주식가격 프로그래머스 스택/큐 [파이썬]**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[programmers-stockprice]:https://programmers.co.kr/learn/courses/30/lessons/42584
