---
layout: single
title: "What is web service"
category: "django"
tag: [web, url, http, html, server, web framework]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# What is Web Service  


## what is web  

* WEB = world wide web = 정보의 그물망  


* 웹은 위에서부터 아래로 순차적으로 정보를 진행시키는 것이 아니라 원하는 정보가 있는 그 위치로 그때그때 비순차적으로 정보를 전달하고 받아들임
> 하이퍼 링크(Hyperlink)를 통해 정보와 정보, 자원과 자원이 마치 그물처럼 서로 얽히고 섥히게 되는 구조를 우리는 웹이라고 지칭함  

* 웹은 URL, HTTP, HTML이라는 세 가지 기능을 제공함

## what is URL, HTTP, HTML  
    
1. URL : 정보 자원이 어디 있는지를 나타내는 표식 = 정보의 위치정보  

2. HTTP : 정보자원으로 접근하고 통신할 수 있게 해주는 약속  
    > URL을 통해 정보 자원의 위치를 얻고 내가 수행하고자 하는 작업을 통신을 통해 요청을 보냄. 이때 통신규약 즉 프로토콜을 HTTP라고 부름.  
    
    
    * HTTP 요청에는 여러 종류가 있지만 대표적으로 GET과 POST가 있음
        * URL에 GET요청을 하면 html이라는 문서를 전달해줌
        * URL에 댓글을 남기면 그 댓글이라는 데이터를 처리해달라는 요청을 보낼 때 POST 사용


3. HTML : 응답으로서의 정보 자원 자체 OR 다른 정보 자원과 연결 매개체
    * 웹 상의 정보를 보여주고 a 태그를 통해서 다른 자원과 연결지어질 수도 있음


## what is server   

* 서버란 무엇이냐
    * 정보를 url로써 미리 간직하고 경우에 따라서 html도 미리 준비해두고 간직하고 있는 url로 http 요청이 들어오게 된다면 거기에 대한 응답을 해주는 것  
    

* web browser란? 
    * 서버까지의 http 통신을 보내주기도 하고 html을 받아서 우리들 눈에 보여주기도 하는 도구  
    
    
## Then what is Web Service  


* Web Service : html과 url을 미리 준비해 놓고 사용자 요청에 대한 응답을 보낼 수 있는 프로그램


# What is Web Framework

* 웹 프레임워크 = 웹 서비스를 쉽게 만들어주는 기계

> "컴퓨터 프로그래밍에서, 소프트웨어 프레임워크는 복잡한 문제를
>  해결하거나 서술하는 데 사용되는 기본 개념 구조이다.
>  간단히 뼈대, 골조, 프레임워크라고도 한다"  


* 정형화 되어있는 웹 개발을 효율적으로 하기 위해 미리 만들어 놓은 웹 개발의 기능단위, 설계단위의 집합  

* 라이브러리와 무엇이 다를까? 
    * 프레임워크는 명확한 목적을 달성하기 위해 이미 설계까지 만들어지 구조/뼈대
    * 라이브러리는 연장의 모음
        * React는 프론트엔드 라이브러리로써 사용자 인터페이스를 만들기 위한 javascript 라이브러리 → 필요에 따라 그 기능을 직접 갖다씀
        * django는 백엔드 프레임워크
