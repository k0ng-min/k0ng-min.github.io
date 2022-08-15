---
layout: single
title: "URL mapping, Static"
category: "django"
tag: [django, url mapping, static]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---



# URL Mapping  



> Jekyll에서 사용되는 liquid는 {{와 }}를 escape 문자로 사용하는데, <br/>
> md문서에 {{, }}가 있는 경우 에러 메시지를 출력함.<br/>
> 따라서 다음과 같이 여는 중괄호가 시작하기 전에 raw를, 뒤에는 endraw를 추가하는 해결책을 강구함<br/>
> [[Github블로그/Jekyll] Liquid Exception: Liquid syntax error 해결](https://iamheesoo.github.io/blog/gitblog-sol-jekyll02)



## Django Application 생성  

* python manage.py startapp 앱이름
    * 다음 코드를 통해 앱이름이라는 폴더 생성  
    
* 프로젝트의 ettings.py에 있는 INSTALLED_APP에 생성한 앱이름을 추가하기
    
    
## views.py 안에 함수 작성하기  

* from django.shortcuts import render가 있는지 확인하고 없으면 추가하기  

* html과 렌더링할 수 있도록 함수 작성하기
```python
   def index(request):
	  return render(request, 'home.html')
    # 앱 안에 있는 home.html로 렌더링해주기
```  



## URL mapping  

1. 프로젝트 폴더의 urls.py을 열어 상단에 'from 앱이름 import views' 추가하기  

2. urlpatterns의 리스트 내부에 path('임의의 주소값/', views.index), 추가하기
    * 다음 코드는 사용자가 '주소값' URL로 접근할 시 앱 안의 views.py 내부에 있는 index 함수를 호출하고 함수의 반환값을 응답하도록 mapping 해줌.
    * URL 매핑 시 /주소값/으로 설정하면 안 됨!
    * /주소값/로 설정할 경우 localhost:4000//주소값와 같이 슬래쉬를 두번 써야 함.  


# Static

* 웹 서비스 내부 데이터
    1. static : 사용자들을 위해 미리 준비된 데이터
    2. media : 사용자가 업로드한 사용자에 의한 데이터

## settings.py에서 static파일 관리  
    
    
1. STATICFIILES_DIRS : static 파일들의 경로
```python
   STATICFILES_DIRS = [
       BASE_DIR / 'static',
   ]    
    # 가장 윗부분에 위치해있는 디렉토리를 BASE_DIR라고 칭함
    # static파일을 최상위폴더인 BASE_DIR 안의 static이라는 폴더 안에서 관리함
```    
    
    
    
2. STATIC_ROOT : static 파일들을 복사하여 모아 놓을 경로
    * 특정파일에 static파일을 모아 놓고 배포를 진행하는데 어떤 폴더에 static 파일을 모조리 모아 놓을 것인지 알려주는 경로를 정함  
    * 배포를 하려고 할 시 중요
    
```python
   STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
    # 상단에 import os 추가하기
    # python manage.py collectstatic를 통해 STATIC_ROOT에 적어 놓은 경로에
    # static파일을 모조리 모아놓을 수 있음(배포 시 필요)
```    


3. STATIC_URL : static 파일을 제공할 url
    * STATIC_URL = '/static/'
    
    
> 규모있는 웹서비스를 만들 때 장고는 static 파일이 <br/>
> 어디 있는지 효율적으로 찾기 위해서는 이러한 관리가 필요!


### application안에 static 파일 관리

```python
   STATICFILES_DIRS = [
       os.path.join(BASE_DIR, 'staticapp', 'static'),
   ]    
    # staticapp안에 static 폴더를 생성 시 사용하는 코드
```    


## static 파일 불러오기

* home.html에 static 파일을 불러오기 위해서는 
    1. home.html 맨상단에 {% raw %}{% load static %}{% endraw %} 추가하기 
        * {% raw %}{% %}{% endraw %}를 template 언어라고 칭함  
        
        
    2. static 파일을 head 부분에 link하기
```python
   <link rel="stylesheet" type="text/css" href="{% raw %}{% static 'css/style.css'%}{% endraw %}">
   <img src="{% raw %}{% static 'img/logo.png'%}{% endraw %}">
   #  static 폴더 안의 css 디렉토리 안의 style.css를 갖고 온다는 의미
```   

