# 로또 번호 추첨기

역할 : 1부터 45개의 공 중 6개 뽑기

1. **공 1개 뽑기**

    → [ Math.random(); ⇒ 0이상~1미만 실수(float) ]

    → 따라서 [ Math.random()*45+1; ⇒ 1이상~46미만 실수(float) ]으로 범위를 설정하기

    → 실수형을 정수형으로 바꾸는 함수인 parseInt()를 사용하기 → 소수점 아래 숫자는 모두 제거함

```python
<script>
var num = Math.random() * 45 + 1;
var ball1 = parseInt(num);
document.write(ball1);
</script>
```

2. **공 여러 개 반복하여 뽑기**

    → for문 사용
```python
<script>
var lotto = [];
for (var i = 0; i < 6; i++){
lotto.push(parseInt(Math.random() * 45 + 1));
}
document.write(lotto);
</script>
```
3. **하나의 배열에 중복된 값이 들어가면 안 됨**

    → .push()로 처리하기

    → 조건문과 [ .index0f(값) : 값이 있으면 위치, 없으면 -1 ]사용하기
```python
<script>
var lotto = [];
for (var i = 0; i < 6; i++){
var num = parseInt(Math.random() * 45 + 1);
if (lotto.indexOf(num) == -1) {
lotto.push(num);
}
}
document.write(lotto);
</script>
```
    But 중복되는 것을 하나 버릴 시 하나를 버리게 되는 경우가 생김 - while문 사용
```python
<script>
var lotto = [];
while (lotto.length < 6) {
var num = parseInt(Math.random() * 45 + 1);
if (lotto.indexOf(num) == -1) {
lotto.push(num);
}
}
document.write(lotto);
</script>
```
4. **배열 값 정렬**

    → .sort = 배열 정렬하기
    
```python
<script>
*var lotto = [];
while (lotto.length < 6) {
var num = parseInt(Math.random() * 45 + 1);
if (lotto.indexOf(num) == -1) {
lotto.push(num);
}
}*
var lotto = [1,2,3,33,22,11];
lotto.sort((a,b)=>a-b);
document.write(lotto);
</script>
```
5. **last(꾸몄을 때)**
```python
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>로또 번호 추첨기</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
<h1>로또 번호 추첨기</h1>
<script>
var lotto = [];
while (lotto.length < 6) {
var num = parseInt(Math.random() * 45 + 1);
if (lotto.indexOf(num) == -1) {
lotto.push(num);
}
}
lotto.sort((a,b)=>a-b);
document.write("<div class='ball ball1'>" + lotto[0] + "</div>");
document.write("<div class='ball ball2'>" + lotto[1] + "</div>");
document.write("<div class='ball ball3'>" + lotto[2] + "</div>");
document.write("<div class='ball ball4'>" + lotto[3] + "</div>");
document.write("<div class='ball ball5'>" + lotto[4] + "</div>");
document.write("<div class='ball ball6'>" + lotto[5] + "</div>");
</script>
</body>
</html>
```
