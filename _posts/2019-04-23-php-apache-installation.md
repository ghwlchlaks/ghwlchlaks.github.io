---
layout: post
title: "윈도우 apache php 설치"
date:   2019-04-22 00:00:00
description:  윈도우 apache php 설치 # Add post description (optional)
img: about_cover.jpg # Add image post (optional)
categories: Jiho
tags: [Blog, IT]
navigation: True
subclass: 'post tag-IT tag-Interview'
logo: 'assets/images/default/DMB_logo.png'
cover: 'assets/images/cover/about_cover.jpg'
author: Jiho # Add name author (optional)
disqus: true
---



## 1. [아파치 다운][apache-download]  
C드라이브에 압축해제
<img src="/assets/images/2019-04-23-php-apache-installation/apahcefolder.png">

폴더내부에 Apache24/conf/httpd.conf 파일 수정   
```
Define SRVROOT "C:\자신의 apache폴더위치\Apache24"  
...  
ServerAdmin 자신의 이메일  
...  
ServerName localhost  

```

환경 변수 설정
path 변수 값 apache폴더/bin

관리자 권한으로 명령프롬프트 실행
httpd.exe -k install
httpd.exe -k start

localhost 접속 
it works가 출력되야 정상  

## 2. [php 다운][php-download]
C드라이브에 압축해제
php.ini-production의 이름을 php.ini로 변경 후 내용 수정  
```
extension_dir = "C:\php가 설치된 폴더 경로\php\ext"
```

1번에서 진행했던 httpd.conf파일에 내용 추가

```
LoadModule php7_module "C:\php가 설치된 폴더 경로\php\php7apache2_4.dll"
AddType application/x-httpd-php .php .html
AddHandler application/x-httpd-php .php .html
PHPIniDir "C:\php가 설치된 폴더 경로\php" 
```

httpd.exe -k restart  

Apache24\htdocs에 test.php파일 추가
<img src="/assets/images/2019-04-23-php-apache-installation/code.png">
```
# test.php
<?php phpinfo(); ?>
```

localhost/test.php접속

### 결과화면
<img src="/assets/images/2019-04-23-php-apache-installation/result.png">

위와같이 출력되면 정상적으로 php apache설치 및 연동이 된것입니다. 


[apache-download]:https://www.apachelounge.com/download/
[php-download]:https://windows.php.net/download