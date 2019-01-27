---
layout: post
title: "[Angular] Angular Http Ajax 사용하기"
date:   2019-01-27 00:00:00
description:  Angular Http Ajax 사용하기 # Add post description (optional)
img: angular.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Angular, Typescript]
navigation: True
subclass: 'post tag-IT tag-Typescript tag-Angular'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/angular.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다. 

이번에 포스팅할 내용은 Angular에서 http 방법으로 Api 호출하는 방법에대해서 포스팅하겠습니다. 

## 순서  
>* 라이브러리 설치
>* service 파일 생성
>* module 파일 수정
>* service 파일 수정
>* 사용

**1. 라이브러리 설치**  
http 라이브러리를 사용하기위해 아래 명령어를 이용하여 설치 해줍니다. 
기본적으로 @angular라이브러리들은 설치가 되있겠지만 혹시 설치가 안되있는경우 설치해 줍니다.  
{% highlight ruby %}
npm install @angular/http
npm install rxjs-compat 
{% endhighlight %}  

**2. service 파일 생성**  
http 라이브러리를 관리하기위해 파일을 생성해줍니다.  
{% highlight ruby %}
ng generate service services/파일이름
{% endhighlight %}  

**3. module 파일 수정**  
app.module혹은 컴포넌트에 상위에서 사용하는 module 파일을 수정해 줍니다.  
{% highlight ruby %}
import {HttpModule} from '@angular/http';     
import {ApiService} from '../services/service파일이름'
imports: [HttpModule]  
providers: [ApiSerice]
{% endhighlight %}  

**4. service 파일 수정**  
2번에서 생성한 service파일을 수정해줍니다.  
{% highlight ruby %}
export class HomeModule { }
import { Injectable } from '@angular/core';
import {Http} from '@angular/http';(추가)
@Injectable({
providedIn: 'root'
})
export class ApiService {
constructor(private http: Http) { }
getIpAddress(): Observable<Object> {
    (추가)
    return this.http.get('localhost:3000/')
    .map((data: Response) => data.json());
    }
}
{% endhighlight %}  

**5. 사용**  
Api를 사용할 컴포넌트 파일을 수정해줍니다.  
{% highlight ruby %} 
import {ApiService} from './services/service파일이름'
constructor( private apiSerivce: ApiService) { } 
apiService.getData().subscribe((result) => {
    console.log(result);
})
{% endhighlight %}  
위와같이 작성하게되면 localhost:3000으로 api요청이 들어와 값이 반환되게됩니다.  
물론 3000포트의 서버는 작성이 되있으셔야겠죠??

지금까지 **Angular Http Ajax 사용하기**이라는 주제로 포스팅하였습니다!     

해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[dockerfile-instruction]:https://ghwlchlaks.github.io/dockerfile-instruction