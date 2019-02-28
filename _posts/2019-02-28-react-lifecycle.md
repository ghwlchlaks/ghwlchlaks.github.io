---
layout: post
title: "[React] LifeCycle"
date: 2019-02-28 00:00:00
description: 리액트 라이프 사이클 # Add post description (optional)
img: react_js.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT]
navigation: True
subclass: "post tag-IT tag-Interview"
logo: "assets/images/default/DMB_logo.png"
cover: "assets/images/cover/react_js.png"
author: Jiho # Add name author (optional)
disqus: true
---

면접을 준비하면서 리액트를 빠르게 배워서 개발을 진행했습니다.  
공부하면서 중요한 부분중에 하나가 역시 LifeCycle이었고 어려운 부분이었습니다.

어떠한 내용들이 있는지 정리하는 포스팅을 해보려고 합니다.

## 생성

---

### 1.constructor

```
constructor(props) {
    super(props);
}
```

constructor는 생성자 메소드로 컴포넌트가 처음 생성될떄 만들어집니다.
props또한 전달되어집니다.

### 2.componentWillMount (deprecated)

### 3. render

```
render {
    return()
}
```

리액트를 하시면 위와 같은 코드를 보실 수 있는데요 jsx문법을 사용하여 렌더링하는 부분입니다.

### 4. componentDidMount

```
componentDidMount() {
    Document.get...
    axios.get...
}
```

componentDidMount는 3번 render이후에 즉 컴포넌트가 렌더링된 이후 호출되는 메소드로 DOM 조작 및 axios등을 이용한 비동기 데이터 요청을 주로 작성하는 부분입니다.  
여기서 주의할점은 componentDidMount 메소드에서 setState를 이용하여 state의 값을 변경하게되면 리렌더링이 되므로 작성하지 않는 것이 좋습니다.

## 업데이트

---

### 1. getDerivedStateFromProps

```
static getDerivedStateFromProps(nextProps, prevState) {
    if (prevState.val !== nextProps.val) {
        return {val: nextProps.val};
    }
    return null;
}
```

getDerivedStateFromProps는 Props가 변할때 state값을 변경해서 리렌링 할 수 있는 메소드입니다.  
위와 같이 기본적으로 null을 리턴하며 이전 state의 값과 이후 받은 props의 값을 비교하여 다른 경우에만
state를 변경시켜주는 코드입니다. 여기서 주의하실점은 setState문을 이용하여 state를 변경하는 것이아니라
retrun {val: nextProps.val}의 형태로 반환해준다는 것입니다.

### 2. shouldComponentUpdate

```
shouldComponentUpdate(nextProps, nextState) {
    if ( this.state.val !== nextState.val) {
        return false;
    }
    return true;
}
```

기본적으로 return하는 값은 true이며 true인경우에는 리렌더링을 진행합니다.  
해당 메소드는 성능 최적화를 하기위해서 사용하는 메소드로 굳이 리렌더링을 하지 않아도 되는 state를 막는 것입니다.  
위와같이 state혹은 Props를 비교해서 값이 변경된 경우에만 렌더링을 하게 할 수 있습니다.

### 3. getSnapshotBeforeUpdate

```
getSnapshotBeforeUpdate(prevProps, prevState) {
    return prevState.val;
}
```

해당 메소드는 수정(update)이 발생하기 바로 전에 호출되는 메소드입니다. 해당 메소드에서 반환한 값은
componentDidupdate에 세번째 매개변수로 전달됩니다. (자주 사용하는 부분은 아닌것같습니다.)  
찾아보니 리렌더링되는 동안 스크롤의 위치가 처음으로초기화 되는 것이아니라 기존의 위치로 렌더링되기위해 기존의 위치를 update되기전 넘겨주는 역할을 하는 경우에 사용한다고 합니다.

### 4. componentDidUpdate

```
componentDidUpdate(prevProps, prevState, [snapshot]) {
}
```

해당 메소드는 업데이트 처리를 끝내고 render이 된 이후에 실행되는 메소드입니다.  
즉 모든 props와 state의 값이 변경이된상태이고 prevProps와 prevState 인자를 이용해 이전의 값들은 읽을 수 있습니다.  
또한 세번째 인자인 snapshot은 3번에 getSnapshotBeforeUpdate에서 반환한 데이터입니다.

## 소멸

---

### 1. componentWillUnmount

```
componentWillUnmount() {
}
```

해당 메소드는 컴포넌트가 소멸될때 발생하는 메소드로 인스턴스를 제거하는 코드를 작섷해줍니다.

여기까지 큰틀로 실행되는 리액트의 LifeCycle에대해서 알아보았습니다.  
deprecated 된것이 꽤 있기 때문에 모든것을 적지는 않았습니다.

저 또한 작성하면서 다시 공부할 수 있었습니다.

해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`
