---
layout: single
title: "how to use blog"
category: "blog"
tag: blog
toc: true
author_profile: false
sidebar:
    nav: "docs"
---




# 블로그 사용법  


* [github로 이동](https://github.com/k0ng-min/k0ng-min.github.io)
* [github 블로그 만들기](https://www.youtube.com/watch?v=ACzFIAOsfpM&t=617s) 영상 참조
* Ctrl + r을 누르면 새로고침


## 새로운 포스팅 생성
* github에서 create new file을 눌러 언더바 posts/ 년-월-일-제목.md 을 입력하여 파일 생성
    * 월-일을 작성 시 무조건 utc 시간 기준으로 작성하기

    * 맨 위 상단에 layout이라 title처럼 카테고리랑 태그를 추가하면 됨
        * 여러 개의 카테고리를 추가할 때는 category: "category1", "category2", "category3" 으로 하면 됨
        * 여러 개의 태그를 추가할 때는 tag: [tag1, tag2, tag3] 로 추가하면 됨

    * 맨 위 상단에 toc: true를 추가하면 글의 목차를 볼 수 있음

    * blog 포스팅을 들어갔을 때 왼쪽 프로필이 안 뜨게 하려면 맨 위 상단에 author_profile: false 추가하기

    * 왼쪽에 sidebar를 추가하고 싶다면 맨 위 상단에 sidebar: (엔터 하고) nav: "docs" 입력하기

    * 포스팅한 블로그가 search기능에 노출 되고 싶지 않다면 search: false를 작성하기

    * 맨 상단에 속성값 넣기 [jekyll 이동](https://jekyllrb.com/docs/posts/)
        * 편안한 jekyell을 위한 [markdown 문법](https://teddylee777.github.io/jekyll/Jekyll-%EC%82%AC%EC%9A%A9%EC%9D%84-%EC%9C%84%ED%95%9C-markdown-%EB%AC%B8%EB%B2%95)
   
## 소스코드를 블로그로 발행
1. jupyter notebook에서 만든 파일을 마크다운 파일로 다운받은 후 이름을 년-월-일-제목.md로 변경
2. github의 posts 파일에서 add file의 upload file을 통해 다운로드받은 마크다운 파일을 올려주기
3. title을 변경하려면 layout과 title을 정의하는 코드 맨 위에 추가하기

## image 파일 업로드
* image 폴더 만들어서 이미지 업로드
* [Typora 에디터](https://typora.io/)를 이용하면 훨씬 쉽게 해결 가능

## 테마 변경
* __config.yml에서 대부분의 수정사항이 발생
* minimal_mistakes_skin이라는 코드에서 변경 가능

