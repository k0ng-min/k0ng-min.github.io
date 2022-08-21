---
layout: single
title: "javascript자소서 글자 수 세기"
category: "javascript"
tag: [javascript, DOM, lens]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# 자소서 글자 수 계산기

document object model(DOM) : 웹 화면을 구성하는 html 코드를 쉽게 접근할 수 있도록 만든 모듈

1. **document; = DOM의 진입점 역할**
```python
<textarea id= ‘jasoseol’>

    저는 인성문제가 없습니다.       

</textarea>
```
 → 출력 시 : document.getElementById(’jasoseol’);

document.getElementById(’jasoseol’).value 또는 document.getElementById(’jasoseol’).innerHTML을 입력하면 안에 있는 값을 출력할 수 있음.

console.log(”자소서”);로도 출력가능

ex)
```python
<textarea class="form-control" rows="3" id="jasoseol">저는 인성 문제가 없습니다.</textarea>
<script>
var content = document.getElementById('jasoseol').value;
console.log(content);
</script>
```
2. **변수.length()를 출력하면 문자열의 길이가 나옴.**
```python
<textarea class="form-control" rows="3" id="jasoseol">저는 인성 문제가 없습니다.</textarea>
<script>
var content = document.getElementById('jasoseol').value;
console.log(content.length);
</script>
```
3. **글자 수 200개 세기**

→ span 이용하기
```python
<textarea class="form-control" rows="3" id="jasoseol">저는 인성 문제가 없습니다.</textarea>
<span id="count">(0/200)</span>
<script>
var content = document.getElementById('jasoseol').value;
document.getElementById('count').innerHTML = '(' + content.length + '/200)';
</script>
```
4. **함수 이용하기**

함수 ⇒ 명령어 모음

function 함수 이름() { 명령어; } = 함수 정의

함수 이름( ); = 함수 선언
```python
<script>
function counter() {
var content = document.getElementById('jasoseol').value;
document.getElementById('count').innerHTML = '(' + content.length + '/200)';
};
counter();
</script>
```
5. **글자 수를 쓸 때마다 글자 수를 체크하기**

이벤트 핸들링

키보드를 누를 때마다(이벤트), 글자 수를 세주어라(이벤트 핸들링)

onkeydown=’counter();’ 사용하기
```python
<textarea onkeydown='counter();' class="form-control" rows="3" id="jasoseol">저는 인성 문제가 없습니다.</textarea>
<span id="count">(0/200)</span>
<script>
function counter() {
var content = document.getElementById('jasoseol').value;
document.getElementById('count').innerHTML = '(' + content.length + '/200)';
}
counter();
</script>
```
6. **200자 넘으면 더 이상 안 써지도록 하기**

→ if문 사용하기(200자 이후로는 자르기)

→ .substring( )

ex) content.substring(0,5); = 0 이상 5 미만의 글자 수 잘라냄

ex)
```python
<textarea class="form-control" rows="3" id="jasoseol" onkeydown="counter();">저는 인성 문제가 없습니다.</textarea>
<span id="count">(0/200)</span>
<script>
function counter() {
var content = document.getElementById('jasoseol').value;
if (content.length > 200) {
content = content.substring(0,200);
}
document.getElementById('count').innerHTML = '(' + content.length + '/200)';
}
counter();
</script>
```
