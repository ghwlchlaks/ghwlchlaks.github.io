---
layout: post
title: "[Nosql] 공부 (정리전)"
date: 2019-03-04 00:00:00
description: 면접 질문 대비 # Add post description (optional)
img: database.png # Add image post (optional)
categories: Jiho
tags: [Blog, IT]
navigation: True
subclass: "post tag-IT tag-Database"
logo: "assets/images/default/DMB_logo.png"
cover: "assets/images/cover/database.png"
author: Jiho # Add name author (optional)
disqus: true
---

NoSql은 키-값이나 컬럼, 문서 형식 등의 데이터 모델을 이용, 비 관계형 데이터베이스
Nosql과 RDBMS와의 다른 점

- 스키마가 없다. (데이터 관계와 정해진 규격 (table-colmn의 정의))가 없다.
- 관계 정의가 없으니 Join이 불가능 (reference(참조)와 같은 기능으로 비슷하게 구현 가능)
- 분산처리(수평적 확장)를 쉽게 제공
  왜 사용하는가?
- 많은 양의 데이터를 효율적으로 처리가 필요할 때
- 데이터의 분산처리, 빠른 쓰기가 필요할 떄
- 분산처리를 하므로 특정서버에 장애가 발생했을때에도 데이터 유실이나 서비스 중지가 없는 형태의 구조이기 때문에 사용

대표적인 Nosql

- 키-밸류형: redis
- 문서형: mongodb

Mongodb

- 문서지향 데이터 베이스 : 내장 문서와 배열을 이용해서 복잡한 계층구조를 하나의 레코드로 표현 할 수 있다.(json, array)
- 스키마가 없다. (필드 추가 및 제거가 자유로움)
- RDBMS보다 빠름.

Memcached(Remote Dictionary Server)

- 키-밸류 저장소
- 주 사용 사례 : 캐싱, 세션 관리, pub/sub, 순위표 (대형 포털에서는 static page, 검색결과 등을 캐쉬하는데 많이 사용)
- 데이터가 메모리에만 저장되므로 빠름 (휘발성) -프로세스가 죽거나 장비가 종료되면 데이터가 사라짐
- 만료가 되지 않더라고 더 이상 메모리에 넣을 용량이 없으면 LRU(Least recently used) 알고리즘에 의해 사라진다. (최근에 가장 적게 사용한 데이터 먼저)

Redis와 Memcached의 차이점

- Redis는 디스크와 메모리에 저장되는데도 속도가 빠르다.
- 데이터가 메모리 디스크에 저장되기 때문에 불의의 경우에도 데이터 복구가 가능.
- 저장소 메모리 재사용 없음. 명시적으로만 데이터 제거 가능
- Redis는 문자열 ,Set, Sorted set, Hash, List등 다양한 데이터 타입을 지원하지만 Memcached는 문자열만 지원

Redis장점

- 리스트, 배열과 같은 데이터를 처리하는데 용이
- Mysql에 비해서 속도가 빠르다.
- 여러 프로세스에서 동시에 같은 key에 대한 갱신을 요청할 경우, 원자성 처리로 데이터 부적합 방지(원자성 처리 함수 제공)
- 메모리를 활용하면서 영속적인 데이터 보존
- 스냅샷 기능을 제공하여 메모리의 내용을 \*.rdb파일로 저장하여 해당 시점으로 복구 할 수 있다.
- 명령어를 이용하여 명시적 삭제 혹은 만료일을 설정하지 않으면 데이터가 삭제 되지 않는다.
- Redis는 1개의 싱글 스레드로 수행됨. 따라서 서버하나에 여러 개의 Redis서버를 띄우는 것이 가능 .
- Master - slave 형식으로 구성하여 데이터 분실위험을 없앨 수 있다.
  Mongo vs Redis
- 쿼리를 많이 사용하는 프로젝트 Mongo
- 속도가 제일 우선 -Redis

Redis 세션 저장

- node에서 redis를 사용하지 않고 express-session만을 사용하여 데이터를 저장하고 있다면 서버를 재시작하는 순간 저장했던 내용들이 날아가게 됨.
  서버를 재시작하고도 데이터를 유지하고 싶다면? 데이터베이스를 사용해서 데이터를 유지하는 것. 하지만 MySql, Mongodb와 같은 데이터베이스에 저장하는 것은 비용과 속도가 느림.
  이때 사용하는 것이 Redis - 메모리를 이용하기 때문에 속도가 매우 빠름. 노드 클러스링 시 pid가 달라 세션이 유지되지 않는 문제도 레디스를 통해 세션 공유하여 해결.
