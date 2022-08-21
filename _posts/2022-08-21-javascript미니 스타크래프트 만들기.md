---
layout: single
title: "javascript미니 스타크래프트 만들기"
category: "javascript"
tag: [javascript, jquery, function]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# 미니 스타크래프트 만들기

1. **jQuery**

값을 가져올 때 document.getElementById(’content’).value와 같은 긴 코드를 썼지만 $(’#content’).val();를 사용해도 된다.

→ jQuery 장점으로는 간결한 문법, 편리한 API, 크로스 브라우징이 있다. ( $( 선택자 ).행위(); )

```python
<textarea id="content">jQuery를 배워보자</textarea>

<script
src="[https://code.jquery.com/jquery-3.5.1.js](https://code.jquery.com/jquery-3.5.1.js)"
integrity="sha256-QWo7LDvxbWT2tbbQ97B53yJnYU3WhH/C8ycbRAkjPDc="
crossorigin="anonymous"></script>

<script>
console.log($('#content').val());
</script>
```

2. **jQuery 이벤트**

```python
<button id="click">클릭</button>
<script
src="[https://code.jquery.com/jquery-3.5.1.min.js](https://code.jquery.com/jquery-3.5.1.min.js)"
integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
crossorigin="anonymous"></script>
<script>
function hello() {
console.log('hello');
}
$('#click').click(hello);
</script>
```

2. **익명 함수**

→ 함수를 정의하지 않고도 바로 함수를 호출하는 것을 익명 함수라고 함.
```python
<button id="click">클릭</button>
<script
src="[https://code.jquery.com/jquery-3.5.1.min.js](https://code.jquery.com/jquery-3.5.1.min.js)"
integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
crossorigin="anonymous"></script>
<script>
$('#click').click(function(){
console.log('hello');
});
</script>
```
4. **드론을 클릭했을 때 침 발사하기**
```python
<script>
//$() .click() 익명함수
$('#drone').click(function(){
console.log('침 발사');
});
</script>
```
5. **드론을 클릭했을 때 침이 발사되는 모습**

→ fadein(얼마나 지속되는가, 완료되었을 때 무엇이 실행되는가)
```python
<script>
$('#drone').click(function(){
// $() .
$('#spit').fadeIn();
});
</script>
```
6. **침이 목표물까지 이동하기**

→ .aminate(  변화할 css properties, 지속시간, 변형 형태, 완료되었을 때 무엇이 실행되는가)
```python
<script>
$('#drone').click(function(){
$('#spit').fadeIn();
$('#spit').animate({left: '+=250'});
});
</script>
```
7. **침이 다시 드론으로 반환되기**
```python
<script>
$('#drone').click(function(){
$('#spit').fadeIn();
$('#spit').animate({left: '+=250'});
$('#spit').fadeOut();
$('#spit').css({left: '150px'});
});
</script>
```
8. **침을 맞으면 hp가 줄어듬 + hp가 줄어드는 속도를 침을 맞았을 때랑 맞추기**
```python
<script>
var hp = 3;
$('#drone').click(function(){
$('#spit').fadeIn();
$('#spit').animate({left: '+=250'});
$('#spit').fadeOut(function(){
hp = hp - 1;
$('#hp').text('HP :' + hp);
});
$('#spit').css({left: '150px'});
});
</script>
```
9. **벙커에 hp가 0이 되면 벙커가 사라지기**

→ if 조건문 사용하기
```python
<script>
var hp = 3;
$('#drone').click(function(){
$('#spit').fadeIn();
$('#spit').animate({left: '+=250'});
$('#spit').fadeOut(function(){
hp = hp - 1;
$('#hp').text('HP: ' + hp);
if(hp == 0) {
$('#bunker').fadeOut();
}
});
$('#spit').css({left: '150px'});
});
</script>
```
