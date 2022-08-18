---
layout: single
title: "comment, login, logout"
category: "django"
tag: [django, comment, login, logout]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# comment  

* 댓글 구현하기  

1. models.py에 댓글에 해당하는 comment class 만들기  


2. 어떤 게시물 아래에 해당하는 댓글인지 파악
    * foreign key 필요
    * on_delete=models.CASCADE는 참조하는 대상이 같이 삭제된다는 의미
```python
   class Comment(models.Model):
        comment = models.CharField(max_length=200)
        date = models.DateTimeField(auto_now_add=True)
        post = models.ForeignKey(Blog, on_delete=models.CASCADE)
        
        def __str__(self):
            return self.comment
```   


3. comment를 admin사이트에서 관리하기
    * admin.py에서 from .models import Comment로 추가하기
    * admin.site.register(comment) 추가하기  
    
    
4. comment 내용을 맨 위에서 보려면 models.py에 추가하기  


5. 댓글 또한 손으로 직접 입력하여 데이터베이스에 등록하는 사용자 입력에 해당하므로 comment를 작성할 forms.py 수정하기  
```python
   class CommentForm(forms.ModelForm):
        class Meta:
            model = comment
            fields = ['comment']
```   


6. detail.html에 띄우기 전 views.py에 추가하기
    * views.py에서 from .forms import CommentForm으로 추가하기
    * detail함수에 comment_form=CommentForm()추가하고 렌더링하는 세 번째 인자에 추가하기
```python
    # views.py
    def home(request):
        # blog_id번째 블로그 글을 데이터베이스로부터 갖고와서
        blog_detail = get_object_or_404(Blog, pk=blog_id)
        # blog_id번째 블로그 글을 detail.html로 띄워주는 코드
        
        comment_form = CommentForm()
        
        return render(request, 'detail.html', {% raw %}{'blog_detail': blog_detail, 'comment_form': comment_form}{% endraw %})
    # = Blog에 해당하는 객체를 가져오며  pk값이 blog_id인 Blog 객체를 가져온다는 뜻
```   


7. detail.html 추가하기
    1. urls.py에서 create_comment로 이동하는 url 추가하기
```python
    # urls.py
    path('create_comment/<int:blog_id>', views.create_comment, name='create_comment'),
```   
    2. views.py에 comment 저장하는 함수 추가하기
```python
    # views.py
    def create_comment(request, blog_id):
        filled_form = CommentForm(request.POST)
        
        if fileed_form.is_valid():
            finished_form = filled_for.save(commit=False)
            finished_form.post = get_object_or_404(Blog, pk=blog_id)
            finished_form.save()
            
        return redirect('detail', blog_id)
```   
    3. detail.html에 댓글의 목록 노출시키기  
    
```html
    # detail.html
    {% raw %}{% for comment in blog_detail.comment_set.all %}{% endraw %}
    <p>{% raw %}{{ comment }}{% endraw %}</p>
    <br>
    {% raw %}{% endfor %}{% endraw %}
```   

# login/logout  

* 로그인과 로그아웃을 관장하는 account라는 app을 만들어주기  


* settings.py에 app을 등록하고 index.html 위에 로그인 버튼 만들기 <a href = “{% raw %}{% url ‘login’ %}{% endraw %}”>로그인</a>  


* urls.py에 from accounts import views as accounts_views추가하고 path(’login/’, accounts_views.login, name=’login’), 넣기  


* account 앱 안의 views.py에 login함수 추가하기  

```python
    # views.py
    def login(request, blog_id):
        
        # POST요청이 들어오면 로그인 처리를 해줌
        if request.method = 'POST':
            pass
        
        # GET요청이 들어오면 login form을 담고 있는 login.html을 띄워주는 역할을 함
        else:
            return render(request, 'login.html')
```   


* login.html 추가하기 

```python
    <form action="{% raw %}{% url 'login' %}{% endraw %}" method="POST">
        {% raw %}{% csrf_token%}{% endraw %}
        username : <input type='text' name='username'><br/>
        password : <input type='password' name='password'>
        <br/>
        <input type='submit' value='로그인'>
    </form>
```     


* 데이터베이스에 이미 저장된 계정인지 확인
    * views.py에 from django.contrib import auth추가
    * views.py에 from django.contrib.auth.models import user 추가  


```python
    from django.shortcuts import render, redirect
    from django.contrib import auth
    from django.contrib.auth.models import user
    
    def login(request):
        # POST 요청이 들어오면 로그인 처리를 해줌
        if request.method == "POST":
            userid = request.POST['username']
            pwd = request.POST['password']
            user = auth.authenticate(request, username=userid, password=pwd)
            if user is not None:
                auth.login(request, user)
                return redirect('home')
            else: 
                return render(request, 'login.html')
            
        # GET 요청이 들어오면 login form을 담고 있는 login.html을 띄워주는 역할을 함
        else: 
            return render(request, 'login.html')
```    


* index.html에 다음 코드를 작성하여 로그인 여부 확인하기

```python
    # index.html
    {% raw %}{% if user.is_authenticated %}{% endraw %}
    안녕하세요, {% raw %}{{ user.username }}{% endraw %}님!
    {% raw %}{% else %}{% endraw %}
    아직 로그인이 되지 않았어요
    {% raw %}{% endif %}{% endraw %}
```   


* 로그인 한 사람만 새 글 작성, 로그아웃 버튼이 보이도록 하기

```python
    {% raw %}{% if user.is_authenticated %}{% endraw %}
    <a href="{% raw %}{% url 'modelformcreate' %}{% endraw %}">새 글 작성</a>
    {% raw %}{% endif %}{% endraw %}
```   


* 로그아웃 버튼은 index.html에 로그인 버튼처럼 설정한 후 urls.py에서 account_views.login으로 링크하고 views.py안에 logout함수 만들기 
```python
    def logout(request):
        auth.logout(request)
        return redirect('home')
```   
