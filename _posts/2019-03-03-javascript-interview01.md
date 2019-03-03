---
layout: post
title: "[JavaScript] 질문 대비 (정리전)"
date: 2019-03-03 00:00:00
description: 면접 질문 대비 # Add post description (optional)
img: JavaScript.jpg # Add image post (optional)
categories: Jiho
tags: [Blog, IT]
navigation: True
subclass: "post tag-IT tag-JavaScript"
logo: "assets/images/default/DMB_logo.png"
cover: "assets/images/cover/JavaScript.jpg"
author: Jiho # Add name author (optional)
disqus: true
---

Es6

- let, const 도입
  const와 let은 블록 스코프를 따름
  기존 var는 함수 스코프
- let, const도입으로 호이스팅이 일어나지 않는다.
  호이스팅이란? 변수의 정의가 선언과 할당으로 분리되어 변수의 선언을 항상 컨텍스트 내의 최상위로 끌어올리는 것을 의미.
- const : 한번초기화하면 재할당이 불가능, 재선언도 불가능
- let : 재할당 가능 재선언 불가능

Template Literals
기존

변경

렉시컬 스코프(정적 스코프)

- 소스코드가 작성된 그 문맥에서 결정되는 스코프
- 스코프는 함수를 호출할 때 생기는 것이 아니라 선언할 때 생김.

클로저

- 내부함수가 외부함수의 지역변수의 접근할 수 있고, 외부함수는 외부함수의 지역변수를 사용하는 내부함수가 소멸될 때까지 소멸 되지 않는 특성을 의미한다.

스코프체인

- 변수가 호출되었을 때 자신의 스코프부터 찾고 없으면 점점 올라가서 상위 스코프에서 찾는 것을말한다.
- 내부함수에서는 외부함수의 변수에 접근 가능하지만 외부함수에서는 내부함수의 변수에 접근할 수 없다.

Exports module.exports require 차이

- require는 module을 import할 때 사용한다. 반환 값은 module.exports이다.
  모듈이란?
  관련된 코드들을 하나의 코드 단위로 캡슐화하는 것.
- exports는 module.exports를 참조하고 있다.
  그래서 사용할 때 exports는 객체에 프로퍼티를 추가해서 사용해야하고 module.exports는 변수에 새로운 객체를 할당한다.

Es6
화살표 함수에는 없는 것 : 함수이름 , this, arguments

Promise 객체란

- 비동기 동작이 완료된 이후 성공, 실패 결과를 처리하기 위한 핸들러입니다. 값을 가져오게되면 어떻게 처리를 해주겠다는 일종의 약속
- callback함수를 실행하는 대신에 객체로 사용하는 것이다.

Async await란?
Es8(ecma2017)의 공식정의된 문법으로 async, await를 사용하면 비동기 코드를 작성할 때 비교적 쉽고 명확하게 코드를 작성할 수 있따.

자바스크립트는 싱글스레드 프로그래밍언어이기 떄문에 비동기 처리가 필수적입니다. 비동기 처리는 그 결과가 언제 반환될지 알 수 없기 떄문에 동기식으로 처리하는 기법들이 사용되어야하는데 이 때 사용하는 것이 callback, promise, (async, await)입니다.

callback은 많은 callback함수들이 중첩되면 코드의 가독성이 떨어지게됩니다. 이 문제점을 해결하기 위해 promise 개념이 등장합니다. 그 이후 더 절차적이게 보이는 async await 개념이 등장합니다. 주의할 점은 await 뒷부분은 반드시 promise객체를 반환해야한다는 것과 async 함수 자체도 promise를 반환한다는 것입니다.

Await <expression>

- await 키워드 오른쪽의 표현식은 Promise.resolve()로 감싸여 항상 Promise객체로 간주된다.
- async 함수는 항상 Promise를 리턴하며, 그 성공값은 리턴값과 같다.

```
function foo() {
    if (true) {
        var name = 'hans';
    }
    console.log(name); // hans
}
foo();
```

```
function foo() {
    if (true) {
        const name = 'hans';
    }
    console.log(name); // Uncaught ReferenceError : name is not defined
}
foo();
```

```
var a = 3;
var first = 'jeong';
var last = 'pro';
var string = a + 'my name is ' + first + ' ' + last; // '3my name is jeong pro
```

```
var a = 3;
var first = 'jeong';
var last = 'pro';
const string = `${a}my name is ${first} ${last}`;
Var a =10;
Function foo() {
 Var b= 10;
 Console.log(a) //10
 Console.log(b) //10
}
Console.log(b) //undefined
```

기존

```
Const func1 = function() {
  Console.log(arguments);
}
Func(1,2,3,4)
```

Es6

```
Const func1 = (…args) => {
   Consle.log(args)
}
Func1(1,2,3,4)
```
