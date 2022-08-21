# javascript로 웹서비스 만들기  

**javascript를 사용하는 방법**

1. html

    → <script>(자바 스크립트 코드 ex) document.write( ))</script>라는 태그를 써야 javascript 가능함
2. js 파일 

    →  js파일에 자바 스크립트 코드 ex) document.write( )를 작성한 후 html에 <script src='myScript.js'></script>를 쓰기

**세미콜론과 주석의 사용방법**

1. 세미콜론 : 하나의 명령어가 끝났음
2. 주석은 컴퓨터가 읽을 수 없는 글을 읽을 때 사용(// 사용 -  한 줄 주석 또는 /* */ 사용 - 여러 줄 주석)

    → 주석의 용도 : 코드 설명을 적어줄 때 / 코드를 작성시키고 싶지 않을 때

**변수**

var 변수명 = 값; ex) var name = ‘엄준식’;

→ 최근 (ES6)에서는 var 대신 let, const 사용

ex) 변수 사용법
```python
<script>
var name = '엄준식';
document.write(name);
</script>
```  

**자료형**

문자열 자료형(string) : 큰 따옴표나 작은 따옴표로 감싸주기

숫자형 자료형(int, float) : 정수형, 실수형

불 자료형(bool) : true, false

→typeof 데이터를 작성하면 데이터의 자료형 파악 가능

**배열(Array)**

ex) var lotto = [1,2,3,4,5,6] ⇒ 인덱스는 0부터 시작함

변수.push()를 작성하면 소괄호 안에 있는 것이 변수의 배열에 들어감

**반복문(for)**

for(시작; 끝 ; 증가){

반복하려는 코드}

ex) for (var i= 0; i<6; i++){

반복하려는 코드}

**조건문**

if(조건){ 참일 경우 }

[ .index0f(값) : 값이 있으면 위치, 없으면 -1 ]사용하기

**반복문(while)**

while(조건){반복하는 문장}

[ .length ⇒ 배열의 길이 ] 사용하기

ex) while (변수.length < 상수){반복하는 문장}

**정렬**

.sort() = 배열 정렬하기 → 맨 앞자리 순서대로 정렬됨

ex) [1,2,3,33,22,11] →[1,11,2,22,3,33]

.sort((a,b)⇒a-b) = 숫자를 오름차순으로 정렬함. (안에는 임의의 변수)
