---
layout: post
title: "[React] 컴포넌트간의 데이터 전송"
date: 2019-03-01 00:00:00
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

2개이상의 컴포넌트를 만들게 되면 부모 자식 관계의 컴포넌트가 생성되게 됩니다.  
리액트에서 컴포넌트간 데이터를 전송을 해야하는 경우가 많습니다. 이럴때 어떻게 데이터를 전송할 수 있을지 알아보도록하겠습니다.

> 1. 부모에서 자식으로 데이터 전송
> 2. 자식에서 부모로 데이터 전송

## 1. 부모컴포넌트에서 자식컴포넌트로 데이터 전송

부모에서 자식으로 데이터를 전송하는 방법은 Props를 이용한 방식을 사용합니다.

```
class Parent extends Component {
    const data = this.state.data;
    render() {
        return (
            <div>
                <Child dataFromParent={data} />
            </div>
        )
    }
}
```

위와 같이 `Parent` 컴포넌트에서 자식컴포넌트를 렌더링하고있는 상황에 부모컴포넌트는 data라는 값을 자식컴포넌트 dataFromParent로 전달해줍니다.  
이때 `Child` 컴포넌트에서는 this.props.dataFromParent로 접근하여 데이터를 읽을 수 있습니다.

## 2. 자식컴포넌트에서 부모컴포넌트로 데이터 전송

자식에서 부모로 데이터를 전송하는 방법은 states를 이용한 방식을 사용합니다.

```
class Parent extends Component {
    parentCallback = (dataFromChild) => {
        // 자식 컴포넌트에서 받은 값을 이용한 로직 처리
        this.setState({
            data: dataFromChild
        })
    }

    render() {
        return (
            <div>
                <Child callbackFromParent={this.parentCallback}>
            </div>
        )
    }
}
```

위와 같이 parentCallback 함수를 `Child`에게 전달하여 자식은 this.props.callbackFromParent로 접근 할 수 있습니다. 접근하여 `Parent` state값을 변경할 수 있습니다.

1, 2번 부모가 인자를 넘겨주고 자식이 이용하는 방법은 동일하지만 부모가 자식에게 데이터를 전달하는 것은 자식컴포넌트에서 부모컴포넌트의 데이터를 이용한(읽기) 로직을 처리하기 위함이고, 자식 컴포넌트에서 부모컴포넌트로 데이터를 전달하는 것은 부모 state의 값을 변경하기 위함입니다.

간단하게 부모와자식컴포넌트 사이에서 데이터를 교환하는 방법에대해서 알아보았습니다.

해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`
