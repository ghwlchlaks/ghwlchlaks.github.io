---
layout: post
title: "[React-native] 설치 방법"
date: 2019-03-23 00:00:00
description: 리액트 네이티브 설치 방법 # Add post description (optional)
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

# `해당 게시글은 작성 진행 중입니다.`

사전의 설치되있어야하는 프로그램
안드로이드 스튜디오, jdk
[참고 링크][참고-링크]

```
npm install -g react-native-cli
```

## 안드로이드 스튜디오에서 설치할 라이브러리
Android SDK   
Android SDK Platform - Android SDK Platform 28    
Performance (Intel ® HAXM) (See here for AMD)  
Android Virtual Device  
Intel x86 Atom_64 System Image or Google APIs Intel x86 Atom System Image  

## 안드로이드 sdk 환경변수 설정
<img src="/assets/images/2019-03-23-react-native-installation/sdk_path.png">  

## platform tools path 설정
```
c:\Users\YOUR_USERNAME\AppData\Local\Android\Sdk\platform-tools
```

## 안드로이드 스튜디오 emulator 실행

## 프로젝트 생성
```
react-native init firstProject
```

## 연결된 디바이스 검색
```
adb devices
```
<img src="/assets/images/2019-03-23-react-native-installation/adb_list.png">  

## 프로젝트 안드로이드 emulator로 실행
```
react-native run-android
```
<img src="/assets/images/2019-03-23-react-native-installation/result_android.png">  


해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`

[참고-링크]:[https://facebook.github.io/react-native/docs/getting-started.html]