---
layout: post
title: "[Angular] Angular ng-bootstrap 환경 설정"
date:   2019-01-13 00:00:00
description: Angular ng-bootstrap 환경 설정  # Add post description (optional)
img: angular.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, TypeScript, Angular]
navigation: True
subclass: 'post tag-IT tag-Node tag-TypeScript tag-Angular'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/angular.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다. 

이번에 포스팅할 내용은 Angular에서 ng-bootstrap 라이브러리 설치 및 사용방법에대해서 알아보겠습니다. 

이번 포스팅은 Angular 프로젝트가 cli로 생성했다는 전제하에 진행하도록 하겠습니다. 
Angular 프로젝트 생성 방법 링크는 밑에 있습니다.
[angular 프로젝트 생성][angular-project-create]  

**순서**
>* ng-bootstrap 설치
>* ng-bootstrap 모듈 import
>* style.css에 bootstrap css추가
>* sample code 실행하여 적용되었는지 확인

먼저 설치 설치 원본 링크입니다. 
[ng-boostrap 설치][ng-bootstrap-installation]  

**1. ng-bootstrap 설치**
ng-bootstrap 모듈을 설치하도록 하겠습니다. 
그리고 ng-bootstrap에서 css를 사용하기위해 bootstrap모듈도 설치를 해줍니다.
{% highlight ruby %}
npm install --save @ng-bootstarp/ng-boostrap
npm install --save bootstrap
{% endhighlight %}  

**2. ng-bootstrap 모듈 import**
ng-boostrap을 사용하기위해 모듈을 app.module.ts에 import를 해보겠습니다.
{% highlight ruby %}
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { NgbModule } from '@ng-bootstrap/ng-bootstrap'; //추가
import { AppComponent } from './app.component';
@NgModule({
declarations: [
AppComponent
],
imports: [
BrowserModule,
NgbModule //추가
],
providers: [],
bootstrap: [AppComponent]
})
export class AppModule { }
위와같이 주석으로 추가라고 된 2줄만 추ㅏ해주시면됩니다.
{% endhighlight %}  

**3. style.css에 bootstrap css추가**
1번에서 설치한 모듈인 boostrap의 css를 사용하기위해 style.css에 해당 코드를 추가합니다.
{% highlight ruby %}
@import "~bootstrap/dist/css/bootstrap.css";
{% endhighlight %}  

여기까지 ng-boostrap을 사용하기 위한 준비가 끝났습니다. 
이제 샘플 코드 하나를 적어 잘 적용되었는지 확인하도록 하겠습니다.  

**4. sample code 실행하여 적용되었는지 확인**
html파일에 아래와같은 코드를 적어 줍니다.
{% highlight ruby %}
<ngb-accordion #acc="ngbAccordion" activeIds="ngb-panel-0">
<ngb-panel title="Simple">
<ng-template ngbPanelContent>
Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia
aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor,
sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica,
craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings
occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus
labore sustainable VHS.
</ng-template>
</ngb-panel>
<ngb-panel>
<ng-template ngbPanelTitle>
<span>★ <b>Fancy</b> title ★</span>
</ng-template>
<ng-template ngbPanelContent>
Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia
aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor,
sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica,
craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings
occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus
labore sustainable VHS.
</ng-template>
</ngb-panel>
<ngb-panel title="Disabled" [disabled]="true">
<ng-template ngbPanelContent>
Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia
aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor,
sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica,
craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings
occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus
labore sustainable VHS.
</ng-template>
</ngb-panel>
</ngb-accordion>
복사 붙혀넣기를 해봅시다.!!
{% endhighlight %}  

잘 적용되었다면 아래와같은 화면이 출력됩니다. 
물론 angular 이미지는 angular 프로젝트 생성시 있는 이미지입니다.

<img src="/assets/images/2019-01-14-angular-ngbootstrap-setup/result.png">


지금까지 **Angular ng-bootstrap 환경 설정**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[angular-project-create]:https://ghwlchlaks.github.io/angular-starter
[ng-bootstrap-installation]:https://ng-bootstrap.github.io/#/getting-started
