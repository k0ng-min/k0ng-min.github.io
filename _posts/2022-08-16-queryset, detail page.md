# QuerySet  


* 데이터 베이스 안에 저장된 블로그라는 객체들을 index.html에 모조리 찍어 보여주는 것이 궁극적 목표
    1. views.py 안에 있는 home 함수에 블로그 글들을 모조리 띄우는 코드를 작성해야 함
    2. 데이터 베이스로부터 views.py로 블로그 객체를 모두 가져와야 함
```python
    # views.py
    def home(request):
        # 블로그 글들을 모조리 띄우는 코드
        posts = Blog.objects.all()
        return render(request, 'index.html', {% raw %}{'posts': posts}{% endraw %})
```

    3. index.html에서 post를 사용하려면 {% raw %}{{ posts }}{% endraw %} 입력하기
    4. queryset에 둘러싸인 채 출력됨
    
    
## Queryset


* queryset = 데이터베이스로부터 전달받은 객체들의 집합 또는 목록

* index.html에서 template언어로 for문을 통해 하나씩 출력하기
```python
    # index.html
    {% raw %}{% for post in posts %}{% endraw %}
        <h3>{% raw %}{{ post.title }}{% endraw %}</h3>
        <h4>{% raw %}{{ post.date }}{% endraw %}</h4>
        
        {% raw %}{{ post.body }}{% endraw %}
    {% raw %}{% endfor %}{% endraw %}
```  

* 데이터베이스에 Blog객체들의 object를 갖고 올 때 특정 필터를 통해 갖고 오기 
    * order_by는 정렬되어 옴 
```python
    # views.py
    posts = Blog.objects.filter().order_by('date')
    # 오름차순으로 갖고 왔을 때
    posts = Blog.objects.filter().order_by('-date')
    # 내림차순으로 갖고 왔을 때
```

# detail page  


* 우리가 primary key를 지정해주지 않는다면 장고가 보이지 않는 primary key를 만들어 줌
    1. 숨겨져 있는 primary key인 id가 차례로 생성됨
    2. 객체가 만들어진 순서를 담고 있는 숫자를 id로 지칭함
        * 첫 번째로 생성된 blog 객체는 id가 1임  
        
        
```python
    # urls.py / blog_id는 detail 함수에 넘길 값
    path('detail/<int:blog_id>', views.detail, name='detail'),
    
    #127.0.0.1:8000/detail/1
    #127.0.0.1:8000/detail/2
    #127.0.0.1:8000/detail/3
```  
```python
    # index.py
    {% raw %}{% for post in posts %}
        <a href="{% raw %}{% url 'detail' post.id %}{% endraw %}"><h3>제목: {% raw %}{{ post.title }}{% endraw %}</h3></a>
        <h4>작성날짜 : {% raw %}{{ post.date }}{% endraw %}</h4>
    {% raw %}{% endfor %}{% endraw %}
    # 제목을 누르면 detail이라는 문자열을 갖고 있는 url로 넘어가는데 post.id라는 내용도 추가적으로 필요할 것이라는 의미
```    



* views.py에 blog_id번째 블로그 글을 데이터베이스로부터 갖고 와서 blog_id 번째 블로그 글을 detail.html로 띄워주는 코드 만들기
    * views.py에서 from django.shortcus import render, redirect, get_object_or_404()로 수정하기 
        * get_object_or_404() = pk 값을 이용해 특정 모델 객체 하나만 갖고 오기
```python
    # views.py
    def home(request):
        # blog_id번째 블로그 글을 데이터베이스로부터 갖고와서
        blog_detail = get_object_or_404(Blog, pk=blog_id)
        # blog_id번째 블로그 글을 detail.html로 띄워주는 코드
        return render(request, 'detail.html', {% raw %}{'blog_detail': blog_detail}{% endraw %})
    # = Blog에 해당하는 객체를 가져오며  pk값이 blog_id인 Blog 객체를 가져온다는 뜻
```  


* detail.html 생성하기

```python
    # detail.html
    <h1>제목</h1>
    {% raw %}{{ blog_detail.title }}{% endraw %}
    
    <h2>날짜</h2
    {% raw %}{{ blog_detail.date }}{% endraw %}
    
    <h3>본문</h3>
    {% raw %}{{ blog_detail.body }}{% endraw %}
``` 

# FILE Upload-Media

```python
    # settings.py
    MEDIA_ROOT = os.path.join( BASE_DIR, 'media')
    MEDIA_URL = '/media/'
``` 
<settings.py>
* MEDIA_ROOT = 사용자가 업로드한 파일이 저장되는 경로
* MEDIA_URL= 사진 같은 것들을 업로드한다면 접근할 수 있는 URL경로  


```python
    # urls.py
    urlpatterns += static(settins.MEDIA_URL, document_root=settings.MEDIA-ROOT)
    # media 파일에 접근할 수 있는 url도 추가해주어야 함
``` 
<urls.py>
* 맨 위에 from django.conf import settings 와 from django.conf.urls.static import static 쓰기  


```python
    # models.py
    class Blog(models.Model):
        title = models.CharField()
        body = models.TextField()
        photo = models.ImageField(blank=True, null=True, upload_to='blog_photo')
    # 사진은 업로드하든 안하든 상관없음
    # makemigration 해주기
```   
<models.py>
* blogproject에 media 폴더를 추가하고  그 안에 blog_photo 추가하기  


* 사용자가 사진 직접 업로드해주기
1. forms.py에서 field를 ‘__all__’로 바꾸기
2. form_create.html에서 form 첫 태그 마지막에 enctype=”multipart/form-data” 써주기
3. views.ppy에서 modelformcreate 함수에서 if 조건문에 or request.method == “FILES” 추가하고 아랫줄을 form = BlogModelForm(request.POST, request.FILES)로 바꾸기   


* detail 창에서 사진 보기
1. detail.html에 내용 추가하기

```python
    # index.py
    {% raw %}{% if blog_detail.photo %}{% endraw %}
        {% raw %}{{ blog_detail.photo.url }}{% endraw %}
        <img src = "{% raw %}{{ blog_detail.photo.url }}{% endraw %}" alt="" height="600">
    {% raw %}{% endif %}{% endraw %}
    # url 대신 path를 쓰면 파일 경로가 보임
```  
