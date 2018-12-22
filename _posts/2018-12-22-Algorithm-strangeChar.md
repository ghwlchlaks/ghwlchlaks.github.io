---
layout: post
title: "[프로그래머스 LEVEL2] 이상한 문자 만들기 [파이썬]"
date:   2018-12-22 00:00:00
description: 이상한 문자 만들기 [파이썬] # Add post description (optional)
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

이번에 포스팅할 내용은  **프로그래머스 문제 LEVEL2에 해당되는 이상한 문자 만들기 알고리즘 문제**를 풀어보도록 하겠습니다.

해당 문제는 [프로그래머스 웹페이지][programmers-strangeChar]에서 만나보실 수 있습니다.

# 문제
문자열 s는 공백 문자로 구분되어 있습니다. 각 단어의 홀수는 소문자로, 짝수는 대문자로 바꿔 리턴하는 함수를 작성하시오.

입출력 예제는 [프로그래머스 웹페이지][programmers-strangeChar]에서 확인하세요!

**제한 사항**
>* 문자열 전체가 아닌 단어 공백으로 인덱스를 판별해아합니다.

저의 처음 풀이 방법은  아래와 같습니다. 
{% highlight ruby %}
answer = ""
for datas in s.split():
    c_data = ""
    for i in data:
        if i %2 == 0:
            c_data += data[i].upper()
        else:
            c_data += data[i].lower()
    answer += c_data + " "
    retrun answer.strip() 
{% endhighlight %}  
처음 저의 생각은 단순히 문장을 split() 하여 각 단어별로 짝수, 홀수를 판단하여 대문자(upper), 소문자(lower)로 해결해겠다는 생각을 하였습니다. 이렇게 하게되면 입축력 예제는 통과하지만 제출을 하게되면 많은 실패가 출력되는 것을 보실 수 있을것입니다. 

또는 위에 코드를 이렇게 줄일 수 있습니다. 
{% highlight ruby %}
return ' '.join(''.join([c.upper() if i % 2 == 0 else c.lower() for i, c in enumerate(w)]) for w in s.split())
{% endhighlight %}   

훨씬 깔끕해졌죠? 하지만 실패한 것을 해결하기 위해 조건을 생각해보았습니다.
>1. 위에 해당하는 것처럼 인덱스 별로 짝수, 홀수를 판단하여 대문자, 소문자로 변경해야합니다.
>2. (중요!) 이전까지 작성한 코드는 마지막 공백(" ")을 strip()으로 제거하는 것을 보실 수 있습니다. 
하지만 문자열 마지막에 공백문자가 있다면 당연히 오류가 나겠죠? 이 조건을 생각하여 해결하면 해당 문제를 풀 수 있습니다.

다음은 통과한 풀이 방법 입니다.

# 풀이
{% highlight ruby %}
    dx = 0
    answer = ""
    for i in range(len(s)):
        if s[i] == " ":
            dx = 0
            answer += " "
            continue
        if dx %2 == 0:
            answer += s[i].upper()
        else:
            answer += s[i].lower()
        dx += 1
    return answer
{% endhighlight %}   
문자열을 split()로 쪼개지않고 전체를 for문을 돌린후 단어별로 짝수 홀수를 판단하여 대문자, 소문자로 변환합니다.(조건1)  
그 후 마지막 문자열에 공백이 존재할 수 있기 때문에 그대로 문자열에 더하여 저장하는 코드입니다. (조건2) 
이러한 방식으로 풀면 해당 문제를 해결 할 수 있습니다. 
계속 실패하길래 어디가 문제인가 싶었더니 조건을 더 생각해야한다는 것을 알았습니다.. ㅠㅠ

이부분에서 많은 분들이 실수하시는 것같습니다.

지금까지 **프로그래머스 문제 LEVEL2에 해당되는 이상한 문자 만들기 알고리즘 문제**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[programmers-strangeChar]:https://programmers.co.kr/learn/courses/30/lessons/12930