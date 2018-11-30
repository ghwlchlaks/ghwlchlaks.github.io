---
layout: post
title: "[프로그래머스 LEVEL2] 프린터 프로그래머스 스택/큐 [파이썬]"
date:   2018-10-19 12:00:00
description:  프린터 프로그래머스 스택/큐 [파이썬] 프로그래머스 LEVEL2 # Add post description (optional)
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

이번에 포스팅할 내용은 스택/큐에 해당되는 **프로그래머스 문제 LEVEL2에 해당되는 프린터 알고리즘 문제**를 풀어보도록 하겠습니다.

해당 문제는 [프로그래머스 웹페이지][programmers-printer]에서 만나보실 수 있습니다.

# 문제
일반적인 프린터는 인쇄 요청이 들어온 순서대로 인쇄합니다. 그렇기 때문에 중요한 문서가 나중에 인쇄될 수 있습니다. 이런 문제를 보완하기 위해 중요도가 높은 문서를 먼저 인쇄하는 프린터를 개발했습니다. 이 새롭게 개발한 프린터는 아래와 같은 방식으로 인쇄 작업을 수행합니다.
>1. 인쇄 대기목록의 가장 앞에 있는 문서(J)를 대기목록에서 꺼냅니다.
>2. 나머지 인쇄 대기목록에서 J보다 중요도가 높은 문서가 한 개라도 존재하면 J를 대기목록의 가장 마지막에 넣습니다.
>3. 그렇지 않으면 J를 인쇄합니다.

**제한 사항**
>* 현재 대기목록에는 1개 이상 100개 이하의 문서가 있습니다.
>* 인쇄 작업의 중요도는 1~9로 표현하며 숫자가 클수록 중요하다는 뜻입니다.
>* location은 0 이상 (현재 대기목록에 있는 작업 수 - 1) 이하의 값을 가지며 대기목록의 가장 앞에 있으면 0, 두 번째에 있으면 1로 표현합니다.
  
# 풀이
{% highlight ruby %}
def solution(priorities, location):
    answer = len(priorities)
    array = []
    for i in range(len(priorities)):
        array.append(i)

    while location in array:
        paper = priorities.pop(0)
        idx_paper = array.pop(0)
        isMax =  False
        for i in range(len(priorities)):
            if paper < priorities[i]:
                isMax = True
                break
        if isMax:
            priorities.append(paper)
            array.append(idx_paper)

    return answer - len(array)
{% endhighlight %}   

해당 문제는 큐를 이용하여 해결하였습니다.   
저의 해결 방법은 순서를 나타내는 변수를 더 생성했습니다. (다른분들 풀이 보니깐.. 저건 비효율적인것같네요.ㅠㅠ)  
while문을 통해 배열에 찾고자하는 location이 없다면 while문을 빠져나오는 조건입니다.   
while문안에서는 맨앞에 요소를 pop(0)을 통해 꺼내고 남은 priorities 배열요소와 우선순위를 비교해서 큰 우선순위가 있으면 뒤로 append하고 없으면 pop(0) 연산만 하는 코드입니다.

다른분들에 코드를 보면 저의 부족함이 많이 느껴지네요.. ㅠㅠ

지금까지 **프린터 프로그래머스 스택/큐 [파이썬]**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[programmers-printer]:https://programmers.co.kr/learn/courses/30/lessons/42587