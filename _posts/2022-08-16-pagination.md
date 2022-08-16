---
layout: single
title: "pagination/database"
category: "django"
tag: [django, pagination, database, MARIA DB]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# pagination  


* pagination : 글들의 목록을 페이지 별로 끊어서 보여주는 것  
    * 장고에서 pagination을 쉽게 이용할 수 있도록 라이브러리 패키지를 만들어둠  
    
## 장고에서 제공하는 pagination 기능 사용하기

1. views.py에서 from django.core.paginator import Paginator을 import하기  

2. views.py에서 posts를 끊어주기 위해 posts를 출력하는 함수에 내용 추가하기  
```python
    # views.py
    def home(request):
        posts = Post.objects.filter().order_by('date')
        paginator = Paginator(posts, 5)
        # posts를 5개씩 잘라서 paginator라는 변수에 담기
        pagnum = request.GET.get('page')
        # ?page=의 뒷부분에 해당하는 숫자를 가지고 와서 pagnum에 담기 
        posts = paginator.get_page(pagnum)
        # pagnum를 통해 몇 번에 해당하는지 확인하여 paginator로 갖고와서 posts에 담기
        
        return render(request, 'index.html', {% raw %}{'posts': posts}{% endraw %})
```  



## 페이지 넘기기  


* 첫 페이지, 이전페이지, 다음페이지
```python
    # index.html
    {% raw %}{% if posts.has_previous %}{% endraw %}
    <a href="?page=1">첫 페이지</a>
    <a href="?page={% raw %}{{posts.previous_page_render}}{% endraw %}">이전 페이지</a>
    {% raw %}{% endif %}{% endraw %}
    
    <span>{% raw %}{{ posts.number }}{% endraw %}</span>
    <span> / </span>
    <span>{% raw %}{{ posts.paginator.num_pages }}{% endraw %}</span>
    
    {% raw %}{% if posts.has_previous %}{% endraw %}
    <a href="?page={% raw %}{{posts.next_page_render}}{% endraw %}">다음 페이지</a>
    <a href="?page={% raw %}{{ posts.paginator.num_pages }}{% endraw %}">마지막 페이지</a>
    {% raw %}{% endif %}{% endraw %}
```  


# 외부 DB 연결하기


## Maria DB

* MYsql과는 다르게 MariaDB는 오픈소스로 공개되어 있기에 누구나 쉽게 다운받을 수 있음  

1. [Maria DB](https://mariadb.org/download/?t=mariadb&p=mariadb&r=10.10.0&os=Linux&cpu=x86_64&pkg=tar_gz&i=systemd)에서 설치하기
    * root password는 데이터 베이스의 관리자 격인 계정을 자동으로 만들 때 어떤 비밀번호를 쓸 건지에 대해 작성
    * UTF8 설정 체크하기
    * 기억해야 하는 것 : root password, TCP-port   
    
2. 윈도우에서 MySQL Client 실행 후 root password 입력하여 잘 설치되었는지 확인하기 
    * show databases;을 입력해서 잘 뜨는지 확인


3. HeidiSQL이 같이 설치되어있음
    * HeidiSQL을 이용하여 설치해준 MariaDB나 MySQL의 테이블이나 어떤 것이 저장되었는지 확인 가능   
    * 신규를 통해 rootpassword를 입력하면 데이터베이스를 생성할 수 있음  
    

## 설치한 Maria DB를 django와 연결하기  


1. 터미널에서 pip install mysqlclient를 입력해 설치하기  


2. settings.py에서 DATABASES 수정하기
    * 수정 후 migrate해주기
```python
    # settings.py
    DATABASES = {% raw %}{
        'default':{% raw %}{
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'mysql',
            'user': 'root',
            'password': '1234',
            # 다음 password는 root password를 가져다 씀
            'HOST': '127.0.0.1',
            'PORT': '3306',
        }{% endraw %}
    }{% endraw %}
    # settings.py에서 secretkey와 databases는 절대 외부에 노출해서는 안됨
    # 그래서 mysettings.py라는 임의의 파일을 만들어 secretkey와 databases을 settings.py에서 import를 통해 적용시킴
```   

