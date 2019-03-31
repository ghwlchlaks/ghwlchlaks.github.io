---
layout: post
title: "style-components와 React [styled-components]"
date:   2019-03-30 01:00:00
description: style-components와 React . # Add post description (optional)
img: react_js.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT, Github, Jekyll]
navigation: True
subclass: "post tag-IT tag-Interview"
logo: "assets/images/default/DMB_logo.png"
cover: "assets/images/cover/react_js.png"
author: Jiho # Add name author (optional)
disqus: true
---

이번에는 React에서 styled-components 라이브러리를 사용하여 실습을 해보겠습니다.   

먼저 styled-components [링크][styled-components] 입니다.

## 순서  
>* 라이브러리 설치
>* 예제 실습

### 1. 라이브러리 설치
```
npm install --save styled-components
```

### 2. 예제 실습
#### (1)

```
import React, { Component } from 'react';
import './App.css';
import styled from 'styled-components'

class App extends Component {
  render() {
    return (
      <Wrapper>
        <Title>
          Hello World
        </Title>
      </Wrapper>
    );
  }
}

const Title = styled.h1`
  font-size: 1.5em;
  text-align: center;
  color: palevioletred;
`;

const Wrapper = styled.section`
  padding: 4em;
  background: papayawhip;
`;

export default App;

```

#### 결과 화면 (1)
<img src="/assets/images/2019-03-30-styled-components/result1.png">  


css파일을 사용할 경우, css와 컴포넌트 파일이 떨어져있기 때문에 관리가 불편한 점이 있습니다.   
styled-components는 컴포넌트를 생성할때 스타일을 입히기 때문에 css파일을 따로 관리하지 않아도됩니다.

또한 props를 받아서 스타일에 적용시킬수도 있습니다. 
#### (2)
```
import React, { Component } from 'react';
import './App.css';
import styled from 'styled-components'

class App extends Component {
  render() {
    return (
      <div>
        <Button>Normal</Button>
        <Button primary>Primary</Button>
      </div>
    );
  }
}

const Button = styled.button`
  background: ${props => props.primary ? "palevioletred" : "white"};
  color: ${props => props.primary ? "white" : "palevioletred"};

  font-size: 1em;
  margin: 1em;
  padding: 0.25em 1em;
  border: 2px solid palevioletred;
  border-radius: 3px;
`;


export default App;

```

#### 결과화면 (2)
<img src="/assets/images/2019-03-30-styled-components/result2.png">  

위 코드처럼 컴포넌트에 primary props의 존재 유무에 따라 스타일을 동적으로 지정할 수 있습니다.  

다음 예제를 진행해 보겠습니다. 

#### (3)
```
import React, { Component } from 'react';
import './App.css';
import styled from 'styled-components'

class App extends Component {
  render() {
    return (
      <div>
        <Button>Normal Button</Button>
        <TomatoButton>Tomato Button</TomatoButton>
      </div>
    );
  }
}

const Button = styled.button`
  color: palevioletred;
  font-size: 1em;
  margin: 1em;
  padding: 0.25em 1em;
  border: 2px solid palevioletred;
  border-radius: 3px;
`;

const TomatoButton = styled(Button)`
  color: tomato;
  border-color: tomato;
`;


export default App;

```

#### 결과화면 (3)
<img src="/assets/images/2019-03-30-styled-components/result3.png">  

위에 코드는 style을 override한것입니다. 즉, 이전의 설정한 스타일을 포함하면서 새롭게 tomatobutton생성한 스타일로 덮어집니다.

이것으로 간단하게 styled-components 사용방법과 이점에대해서 알아봤습니다. 

해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~
같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[styled-components]:https://www.styled-components.com/docs/basics#installation