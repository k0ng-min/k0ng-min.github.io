---
layout: single
title: "bootstrap/template상속"
category: "django"
tag: [django, bootstrap, css, template]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# Bootstrap  
 
* 미리 만들어놓은 웹사이트의 꾸밈요소 즉 css를 가져다써서 웹서비스에서 쉽게 이용할 수 있음  
* [Bootstrap](https://getbootstrap.com/)



## Bootstrap 설정  


### 프로젝트에 Bootstrap 적용 방법
1. Bootstrap 관련 코드를 직접 다운 받아 설치하기
2. CDN 이용하기 
    * CSS와 JS파일을 온라인 상에서 실시간으로 가지고 와서 사용  
    
    
### HTML 문서에 CSS를 사용하는 3가지 방법
1. 외부 스타일 시트
    * 홈페이지 전체의 스타일을 일관성있게 유지하며 변경시에도 일괄적으로 변경되므로 홈페이지 제작의 효율성을 극대화 할 수 있음
    * <link rel="stylesheet" type="text/css" href="mystyle.css"><br/>
    * stylesheet: 외부 스타일시트를 참조
    


2. 내부 스타일 시트
    * html 문서마다 스타일을 매번 지정해 주어야 하지만, 한 문서에만 해당되는 스타일을 지정할 때 사용하면 됨
    * <style type="text/css">
    


3. HTML 태그 내에 스타일 지정
    * 스타일을 적용하고 싶은 html 태그 안에서 정의하는 방법
    * <p style="color:gray;">이 문단의 색상은 회색으로 지정됩니다.</p>



# template 상속  


*  template 상속 = 중복되는 코드가 있을 때 중복되는 코드를 하나의 html파일에서 관리하고 중복되지 않는 코드만 개별적인 html에서 관리하는 방법

1. base.html에 중복되는 코드 밀어넣기 ex) heade, head, footer

2. base.html에서 개별적인 코드가 들어가는 부분에 {% raw %}{{% block content %}, {% endblock %}}{% endraw %} 추가하기

```python
    # 코드가 공통으로 들어가는 부분
    {% raw %}{% block content %}{% endraw %}
    # 개별적인 코드가 들어가는 부분 / 각각의 html에서 서로 다른 코드가 들어가는 부분
    {% raw %}{% endblock %}{% endraw %}
    # 코드가 공통으로 들어가는 부분
```  

3. 개별적인 html에 중복되는 코드 지운 후 {% raw %}{{% extend 'base.html' %}, {% block content %}, {% endblock %}}{% endraw %} 추가하기  

```python
    {% raw %}{% extend 'base.html' %}{% endraw %}
    # extend를 통해 base.html의 코드 상속
    {% raw %}{% block content %}{% endraw %}
    # 개별적인 코드가 들어가는 부분 / 각각의 html에서 서로 다른 코드가 들어가는 부분
    {% raw %}{% endblock %}{% endraw %}
```  
* {% raw %}{% block content %}{% endraw %}에서 content이름을 바꿀 수 있음
