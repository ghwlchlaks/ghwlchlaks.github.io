---
layout: post
title: "[Express] Typescript를 이용한 express, node초기 설정"
date:   2019-01-03 00:00:00
description:  Typescript를 이용한 express, node초기 설정 # Add post description (optional)
img: nodejs.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Node, TypeScript]
navigation: True
subclass: 'post tag-IT tag-Node tag-TypeScript'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/nodejs.png'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 입니다. 
2019년 기해년에 첫 게시글이 되겠네요.ㅎㅎ  
모두 새해 복 많이 받으세요~   

이번에 포스팅할 내용은 JavaScript가 아니라 TypeScript를 이용하여 Node 서버 초기 환경 설정하는 방법에 대해서 
포스팅 하겠습니다. 

TypeScript와 JavaScript의 차이는 다른 게시글에서 포스팅하도록 하겠습니다. 

먼저 해당 게시물은 node가 설치 되어있다는 가정하에 시작하도록 하겠습니다.  
혹시 설치가 안되있는 분은 설치 방법을 링크하도록 하겠습니다.  

[윈도우 설치][window-node-install]  
[리눅스 설치][linux-node-install]

먼저 typescript를 이용하여 node 서버 구동을 위한 환경 설정은 다양한 방법들이 존재합니다. 
해당 방법도 여러가지 방법 중 하나라고 생각하시고 보시면 좋을것 같습니다. 

**순서**
>* 폴더 생성 및 node 폴더로 초기화.
>* devloperment 의존성 설치
>* express 설치
>* tsconfig.json 생성 및 작성
>* tslint 생성 및 설정
>* package.json 수정
>* node server 구동


**1. 폴더 생성 및 node 폴더로 초기화.**
{% highlight ruby %}
mkdir typescript-node
cd typescript-node
npm init
{% endhighlight %}  
npm init 명령어를 입력하게 되면 여러가지 적는 칸과 선택 하는 항목이 출력되게됩니다. 
특별하게 설정할 것이없다면 모두 default로 설정해주시면 됩니다.

**2. devloperment 의존성 설치**
{% highlight ruby %}
npm install -D typescript
npm install -D nodemon
npm install -D tslint
{% endhighlight %}  
Typescript로 진행 할 예정이니 당연히 typescript를 설치 해야겠죠?
nodemon은 개발시 auto refresh가 되기 때문에 개발 편의를 위해 설치 해줍니다
tslint는 개발 시 정해놓은 어법을 맞추기 위해 설치 해줍니다.  
문서에서는 코딩스타일, 코딩 표준을 맞추기 위한 방법이라고 설명되어있네요 ㅎㅎ

**3. express 설치**  
{% highlight ruby %}
npm install express
npm install @types/express
{% endhighlight %}  
express로 서버를 구성할 것이기 떄문에 express모듈을 추가적으로 설치 해줍니다.

**4. tsconfig.json 생성 및 작성**  
{% highlight ruby %}
{
    "compilerOptions": {
        "module": "commonjs",
        "esModuleInterop": true,
        "target": "es6",
        "noImplicitAny": true,
        "moduleResolution": "node",
        "sourceMap": true,
        "outDir": "dist",
        "baseUrl": ".",
        "paths": {
            "*": [
                "node_modules/*",
                "src/types/*"
            ]
        },
        "lib": [
            "es2015"
        ]
    },
    "include": [
        "src/**/*"
    ]
}
{% endhighlight %}  
tsconfig.json 파일을 생성후 해당 내용을 넣어줍니다. 
typescript는 compile을 통해 javascript파일을 생성하고 구동합니다.  
그렇기 때문에 compile option을 지정하고 compile할 경로 include를 지정해 줍니다.   
대표적으로  include에 파일들을 lib에 express버전을통해 compile하고 outDir에 경로에 javascript파일을 생성합니다. 

**5. tslint 생성 및 설정**  
{% highlight ruby %}
./node_modules/.bin/tslint --init
{% endhighlight %}  
tslint 설정을 위해 생성해줍니다. 
그 후 tslint.json에 내용을 수정해 줍니다.  
{% highlight ruby %}
{
    "defaultSeverity": "error",
    "extends": [
        "tslint:recommended"
    ],
    "jsRules": {},
    "rules": {
        "interface-name": [false],
        "no-console": [false],
        "quotemark": [true, "single"]
    },
    "rulesDirectory": []
}
{% endhighlight %}  
기본적인 lint이외에 다른 옵션들은 검색을 통해 쉽게 찾으실 수 있습니다.

**6. package.json 수정**  
{% highlight ruby %}
{
  "name": "typescript-node",
  "version": "1.0.0",
  "description": "",
  "main": "dist/server.js",
  "scripts": {
    "build-ts": "tsc",
    "start": "npm run serve",
    "serve": "node dist/server.js",
    "watch-node": "nodemon dist/server.js",
    "watch-ts": "tsc -w"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "nodemon": "^1.18.3",
    "tslint": "^5.11.0",
    "typescript": "^3.0.1"
  },
  "dependencies": {
    "@types/express": "^4.16.0",
    "express": "^4.16.3"
  }
}
{% endhighlight %}  
수정해야할 부분은 main, scripts에 있는 내용입니다. 이외에 내용은 앞에서 설치하며 진행했기 때문에 
수정하지 않아도 될 것입니다.  
`scripts` 부분은 node 서버를 구동하기위해 사용하는 script들입니다.

**7. node server 구동**
기본적인 설정이 끝이 났습니다. 이제 서버를 실행시켜 구동해보도록 하겠습니다.
{% highlight ruby %}
npm run watch-ts
{% endhighlight %} 

다른 터미널에서
{% highlight ruby %}
npm run watch-node
{% endhighlight %} 
그 후 `http://localhost:3000`에 접속해보시면 server가 구동된것을 확인 하실 수 있습니다. 

다음 링크는 초기 환경 설정이 된 폴더 입니다. 

[Typescript-node-boilerplate][Typescript-node-boilerplate]

지금까지 **typescript를 이용한 express, node초기 설정**이라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[linux-node-install]:https://ghwlchlaks.github.io/nodejs-installation-ubuntu/
[window-node-install]:https://ghwlchlaks.github.io/nodejs-installation-window/
[Typescript-node-boilerplate]:https://github.com/ghwlchlaks/typescript-express-example