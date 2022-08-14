---
layout: single
title: "Python for Django"
category: "django"
tag: [django, dictionary, python, class, module, package, library, error]
toc: true
author_profile: false
sidebar:
    nav: "docs"
---


# Python for Django  

* 웹 프레임워크<br/>
    = 웹서비스를 쉽게 만들어주는 기계<br/>
    = 사용법이 정형화되어 있는 기계<br/>

## 자료형(딕셔너리)  

* 딕셔너리 자료형
    * 대응이 되는 데이터를 표현해주고 싶을 때, 이때 사용되는 자료형, 딕셔너리
    * 딕셔너리는 데이터들을 대응시켜주는 자료형  
    * 왜 딕셔너리(사전)이라는 이름이 붙었을까
        * 우리는 탐색의 기준을 통해 찾고자 하는 값을 얻기 때문
    * 탐색의 기준, 키워드 = Key
    * 탐색의 기준에 대응되는, 찾고자 하는 값 = Value  
    * __우리는 Key를 통해 Value를 얻는다__

```python
Val = {Key1 : Value1, Key2 : Value2}
```
1. Key는 중복되어서도 변해서도 안된다.
2. Key1 -> Value1 대응 / Key2 -> Value2대응
3. Key값을 통해 Value 값 얻어내기
    ```python
    print(Val[Key1])
    # Key1에 대응되는 Value1 출력
    ```
4. 새로운 데이터 쌍 추가
    ```python
    Val[Key3] = Value3
    Val == {Key1 : Value1, Key2 : Value2, Key3 : Value3}
    ```

## 예외처리  

### python의 오류  

1. 문법 에러(파싱 에러)
    * 실행 자체에 영향을 주는 치명적인 오류
    
2. 예외
    * 프로그램 실행 자체를 멈추진 않는 오류
    * 실행 중 감지되는 오류
    
### python의 오류 Handling  


```python
    try:
        # 일단 시도해 볼 것
        # 오류가 생길 여지가 있는 코드
    except 발생 오류: 
        # 발생 오류가 발생했을 경우 실행할 코드
```
* 만약 오류가 발생 시 대신 실행할 코드를 출력
* except 뒤에 아무것도 쓰지 않는다면 어떠한 오류가 발생해도 그 뒤에 코드를 실행하라는 의미  

```python
    try:
        # 일단 시도해 볼 것
        # 오류가 생길 여지가 있는 코드
    except 발생 오류: 
        # 발생 오류가 발생했을 경우 실행할 코드
    finally:
        # 예외가 발생했든 안했든
        # 최종적으로 무조건 실행할 코드
```  

* try...except...finally 문법을 사용하는 이유
    * 프로그램을 멈춤 없이 실행시킬 수 있다!  
    
    
* [에러와 예외](https://docs.python.org/ko/3/tutorial/errors.html)에 대해 더 자세한 내용을 볼 수 있습니다!

## 클래스와 객체

* 객체지향 프로그래밍을 할 수 있는 프로그래밍 언어 대부분은 클래스와 객체를 가지고 있음!   

> 이 세상에 있는 모든 객체 즉 대상들은 상태와 동작으로 나타낼 수 있다.<br/>
> → 변수와 함수로 상태와 동작을 나타낼 수 있다!  

1. 이 세상에 있는 모든 대상들은 한 두개가 아니다
2. 변수와 함수로 나타낸 상태와 동작을 여러 개 만들 수 있어야 한다.
3. 상태와 동작(변수와 함수)을 한번에 려러 개 정의할 수 있는 방법<br/>
__==객체지향프로그램__   



```python
    class 클래스이름: # 달고나 틀 만들기
        변수들(상태)
        함수들(동작)
        
    객체이름1 = 클래스이름() # 여러 달고나 만들기
    객체이름2 = 클래스이름()
    객체이름3 = 클래스이름()
    
    # 즉 변수와 함수들로 틀(클래스)을 만들고 달고나(객체)들을 찍어낸다!
```  


## 모듈, 패키지, 라이브러리

### 모듈

* 그냥 파이썬으로 정의된 파일, 가장 작은 단위   


* a.py와 b.py라는 2개의 모듈이 있을 때
* 서로 다른 모듈에 있는 내용을 갖다 쓰기 위해서는 import가 필요

```python
    import a # b.py에서 a.py에 있는 함수를 끌여오고자 할 때 코드
    
    a.sum(1, 2)
    
    # a안에 있는 함수를 쓰고자 할 때 a.변수이름
```    


### 패키지  

* 모듈의 집합, 모듈의 게층 단위  


* 패키지 안에 있는 모듈을 쓰기 위해서는
    * import 패키지 이름.모듈 이름  
    
    
### 라이브러리  

* 쓸만한 기능들을 미리 모듈/패키지로 만들어 놓은 것, 즉 미리 준비된 모듈 및 패키지

#### 파이썬 라이브러리는 크게 두 가지로 나뉨  

* python standard library
    * 썬 언어 자체에서 제공하고 있는 내장함수를 포함하는 라이브러리
    * 문자열의 길이를 반환해주는 lens함수처럼 파이썬을 설치할 때부터 존재하는 라이브러리  
    
* [python package index](https://pypi.org/)
    * 사람들이 직접 만들어 업로드를 하고 관리하는 라이브러리  
    
    
* __pip(python package management system)__
    * pypi에 사람들이 자신이 만든 모듈, 패키지, 라이브러리를 업로드하는데 이를 다운받기 위해 필요

```python
    $ pip install somepackage   # 패키지 설치
    $ pip search somepackage   # 패키지 검색
    $ pip install somepackage==1.0.4   # 특정 버전 지정하여 설치
    $ pip uninstall somepackage   # 패키지 제거 
    $ pip freeze   # 현재 설치된 패키지와 버전 목록
```  
