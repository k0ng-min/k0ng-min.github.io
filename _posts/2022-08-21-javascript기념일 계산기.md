---
layout: single
title: "javascript기념일 계산기"
category: "javascript"
tag: [javascript, object]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---

# 기념일 계산기

1. **객체(object)**
```python
<script>
var person = {
name: 'jocoding',
sayHello: function() { console.log('hello'); }
}
console.log([person.name](http://person.name/));
person.sayHello();
</script>
```
2. **date 객체 알아보기**
```python
<script>
//1. Date 객체 생성
var now = new Date();
//2. 연도를 가져오는 메서드 .getFullYear()
console.log(now.getFullYear());
//3. 월 정보를 가져오는 메서드 .getMonth() {0: 1월, 1: 2월, ... 10: 11월, 11: 12월}
console.log(now.getMonth());
//4. 일 정보를 가져오는 메서드 .getDate()
console.log(now.getDate());
//5. 1970년 1월 1일 00:00:00을 기준으로 흐른 시간을 밀리초로 표시하는 메서드 .getTime()
console.log(now.getTime());
//6. 특정 일의 Date 객체 생성
var christmas = new Date('2020-12-25');
console.log(christmas);
//7. 특정 ms의 Date 객체 생성
var ms = new Date(1000);
console.log(ms);
</script>
```
3. **날짜 수 세기**
```python
<script>
var now = new Date();
var start = new Date('2020-06-30');
var timeDiff = now.getTime() - start.getTime();
var day = Math.floor(timeDiff / (1000 * 60 * 60 * 24) + 1);
$('#love').text(day + '일째');
</script>
```  

4. **기념일까지 남은 날짜**  

```python
<script>
var now = new Date();
var start = new Date('2020-06-30');
var timeDiff = now.getTime() - start.getTime();
var day = Math.floor(timeDiff / (1000 * 60 * 60 * 24) + 1);
$('#love').text(day + '일째');
var valentine = new Date('2021-02-14');
var timeDiff2 = valentine.getTime() - now.getTime();
var day2 = Math.floor(timeDiff2 / (1000 * 60 * 60 * 24) + 1);
$('#valentine').text(day2 + '일 남음');
</script>
```
5. **천일 구하기**
```python
<script>
var now = new Date();
var start = new Date('2020-06-30');
var timeDiff = now.getTime() - start.getTime();
var day = Math.floor(timeDiff / (1000 * 60 * 60 * 24) + 1);
$('#love').text(day + '일째');
var valentine = new Date('2021-02-14');
var timeDiff2 = valentine.getTime() - now.getTime();
var day2 = Math.floor(timeDiff2 / (1000 * 60 * 60 * 24) + 1);
$('#valentine').text(day2 + '일 남음');
var ms = start.getTime() + 999 * (1000 * 60 * 60 * 24);
var thousand = new Date(ms);
var thousandDate = thousand.getFullYear() + '.' + (thousand.getMonth()+1) + '.' + thousand.getDate();
$('#thousand-date').text(thousandDate);
</script>
```
6. **천일 남은 일수 계산하기**
```python
<script>
var now = new Date();
var start = new Date('2020-06-30');
var timeDiff = now.getTime() - start.getTime();
var day = Math.floor(timeDiff / (1000 * 60 * 60 * 24) + 1);
$('#love').text(day + '일째');
var valentine = new Date('2021-02-14');
var timeDiff2 = valentine.getTime() - now.getTime();
var day2 = Math.floor(timeDiff2 / (1000 * 60 * 60 * 24) + 1);
$('#valentine').text(day2 + '일 남음');
var thousand = new Date(start.getTime() + 999 * (1000 * 60 * 60 * 24));
var thousandDate = thousand.getFullYear() + '.' + (thousand.getMonth()+1) + '.' + thousand.getDate();
$('#thousand-date').text(thousandDate);
// thousand, now, getTime()
var timeDiff3 = thousand.getTime() - now.getTime();
var day3 = Math.floor(timeDiff3 / (1000 * 60 * 60 * 24) + 1);
$('#thousand').text(day3 + '일 남음');
</script>
```
7. **last**
```python
<script>
var now = new Date();
var start = new Date('2020-06-30');
//우리 몇 일째?
var timeDiff = now.getTime() - start.getTime();
var day = Math.floor(timeDiff / (1000 * 60 * 60 * 24) + 1);
$('#love').text(day + '일째');
//기념일까지 남은 날짜는?
var valentine = new Date('2021-02-14');
var timeDiff2 = valentine.getTime() - now.getTime();
var day2 = Math.floor(timeDiff2 / (1000 * 60 * 60 * 24) + 1);
$('#valentine').text(day2 + '일 남음');
//천일은 언제인가?
var thousand = new Date(start.getTime() + 999 * (1000 * 60 * 60 * 24));
var thousandDate = thousand.getFullYear() + '.' + (thousand.getMonth()+1) + '.' + thousand.getDate();
$('#thousand-date').text(thousandDate);
//기념일까지 남은 날짜는?
var timeDiff3 = thousand.getTime() - now.getTime();
var day3 = Math.floor(timeDiff3 / (1000 * 60 * 60 * 24) + 1);
$('#thousand').text(day3 + '일 남음');
</script>
```
