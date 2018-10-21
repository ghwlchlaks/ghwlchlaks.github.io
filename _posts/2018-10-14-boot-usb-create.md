---
layout: post
title: "[운영체제] 리눅스 부팅 USB 만들기"
date:   2018-10-14 12:00:00 
description:  리눅스 부팅 USB 만들기 # Add post description (optional)
img: usb.jpg # Add image post (optional)
categories: Jiho
tags: [Blog, IT, OS, Linux]
navigation: True
subclass: 'post tag-IT tag-OS tag-Linux'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/usb.jpg'
author: Jiho # Add name author (optional)
disqus: true
---
안녕하세요! **Do My Best 블로그** 열번째 게시물입니다. ㅎㅎ  
벌써 열번째 게시물이네요~ 이제는 횟수를 적지 않을까 합니다. 이렇게 계속 포스팅해서 나중에 확인했을때 많이 쌓여있는걸 보면 뿌듯하겠죠? ㅎㅎ

이번에 포스팅할 내용은 리눅스 운영체제 부팅 USB륾 만드는 방법에대해 포스팅 하겠습니다.  
Rufus라는 툴을 이용하면 쉽게 이미지파일을 USB에 업로드하여 부팅 USB를 만들 수 있습니다.   
윈도우 운영체제인경우 마이크로소프트 사이트에 접속하시면 쉽게 부팅 USB를 만들 수 있습니다.

* **Rufus 다운받기**
* **ISO 파일 다운받기**
* **부팅 USB 만들기**
* **USB 삽입 후 부팅하기**

## **1. Rufus [설치 링크][installation-rufus]에 접속하기.**  
위에 링크로 접속하셔서 Rufus를 다운 받으셔야합니다.!  

<img src="/assets/images/2018-10-14-boot-usb-create/installation-step1.png">
위에 사진에서 Installer를 클릭하시면 자동으로 설치가 진행됩니다.   


Rufus 설치가 완료되고 파일을 실행했을때의 모습입니다.  
<img src="/assets/images/2018-10-14-boot-usb-create/installation-step2.png">

## **2.ISO 파일 다운받기**  
운영체제를 컴퓨터에 설치하기 위해서는 자신이 설치하고자 하는 운영체제 파일이 있어야겠죠?  
그렇다면 운영체제 이미지 파일을 설치해 봅시다!

1. [debian][debian]
2. [ubuntu][ubuntu]
3. [arch][arch]
4. [fedora][fedora]
5. [centOS][centOS]
6. [redHat][redHat]
   
해당 링크 중 자신이 설치하고자 하는 운영체제 링크에 접속하여 ISO 파일으르 다운 받으시면 됩니다.!  

## **3. 부팅 USB 만들기**  
Rufus와 운영체제 ISO 파일을 다운받으셨다면 이제 부팅 USB를 만들어보겠습니다!  


* 장치 : OS를 설치할 “USB를 선택”합니다.
* 디스크 형식와 부팅 시스템 유형 : MBR 파티션 형식의 BIOS 또는 UEFI(BIOS 호환)을 선택합니다.  
* MBR(MASTER BOOT RECORD) : 가장 보편화된 디스크 파티션 기술로 디스크의 첫번재 센터를 말한다.
* GPT(GUID PARTION TABLE) : MBR의 기술적 제한의 해결하기 위해 나온 디스크 파티션 기술을 말합니다
* BIOS(BASIC INPUT/OUTPUT SYSTEM) : 메이보드에 내장된 펌웨어로 CUI 기반입니다.
* UEFI(UNIFIED EXTENSIBLE FIRMWARE INTERFACE) : BIOS의 발전형이며 GUI 기반의 펌웨어입니다.

* 파일 시스템 : FAT32 을 선택합니다.
* 할당 단위 크기 : 4096 bytes 을 선택합니다.
* 배드섹터 검사 : 이미지가 제대로 설치 되었는지 무결성을 검사합니다. 체크 해제 합니다.
* 빠른 포멧 : USB 포멧 방식입니다. 체크 합니다.

기본적으로 특별한 설정을 하지 않는 이상 default값으로 설정하시면 됩니다.!
모든 설정을 마친 후 실행을 누르시면 자동으로 USB 포맷이 진행되고 부팅 USB가 만들어집니다.


## **4. USB 삽입 후 부팅하기**  
이제 모든 준비가 완료되었습니다.  
이제 컴퓨터를 재시작하고 바이오스 화면에서 부팅 순서를 변경해 줍니다.!  
컴퓨터를 부팅하는 화면에서 "F2"나 "DEL"키를 누르시면 바이오스 설정화면으로 넘어가집니다.   
부팅 화면이 빠르게 넘어갈 수 있으니 해당 키를 연타하시는게 좋을 것 같네요 ㅎㅎ  
바이오스 화면은 메인보드에 따라 다르므로 자신의 메인보드를 검색하셔서 찾아보는것도 좋은 방법입니다!  
기본적으로 'Boot Device Priority'에서 '1st Boot Device'로 boot순서를 변경 할 수 있습니다.   
이때 `1st Boot Device`를 아까 만든 `부팅 USB`로 설정하시면 되겠죠?  
설정을 저장한 후 다시 재부팅하시면 자동으로 운영체제의 설치 화면으로 넘어가게됩니다.!!  

복잡한 과정인것 같지만 해보면 그렇게 복잡하지는 않습니다. ISO 파일 설치할 때 좀 걸린다는 점만 빼면..ㅎㅎ

지금까지 **부팅 USB 만들기**라는 주제로 포스팅하였습니다!    
해당 게시물에 문제가 있다면 댓글을 통해 피드백해주시면 감사하겠습니다~ 같이 공부해요~^^

`방문해주신분들 댓글 한개씩 달아주시면 감사하겠습니다~~^^`  

[installation-rufus]:https://www.techspot.com/downloads/6062-rufus.html
[debian]:https://www.debian.org/CD/http-ftp/
[ubuntu]:https://www.ubuntu.com/download
[arch]:https://www.archlinux.org/download/
[fedora]:https://getfedora.org/
[centOS]:https://wiki.centos.org/?id=15
[redHat]:https://www.redhat.com/en/store


