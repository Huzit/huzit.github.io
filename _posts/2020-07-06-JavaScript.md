---
layout: post
current: post
cover:  assets/images/html_img/javascript.jpg
navigation: True
title: 자바스크립트 간편정리
date: 2020-07-06 16:00:00
tags: [Getting started]
class: post-template
subclass: 'post'
author: huzit
---

## 1. 자바스크립트를 해야하는 이유

자바 스크립트는 가볍고 모든 브라우저에서 사용가능한 유일한 언어이다.<br>
웹에서 사용자와 상호작용을 하기위해선 필수적으로 필요하다.
따라서 모두가 알기 때문에 Fragmentation(분열) 이 없다.

하지만 언어차원에서 immutable함을 제공해주지 않는다는 치명적인 단점이 있다.<br>
JS객체는 언제건 속성을 추가, 삭제, 수정할 수도있고 클래스 밖에서도 클래스의 속성을 바꿀 수 있다. 

> 대표적으로 this바인딩이 있다.



이 문서에서 다루는 JS는 Vanilla JS에 초점을 둘 것이다.<br>
Vanilla JS로 한 이유는 나중에 React나 Angular, Vue 등을 배울때 어렵지 않게 배울 수 있기 때문이다.

> Vanilla JS룰 배운다는것은 웹의 원초를 배운다는 것, 복잡하고 귀찮지만 강력하다
시간나면 사이트에 들어가 보는것도 추천한다. *0byte!!!*<br><http://vanilla-js.com/> 

<br>

## 2. 문법 및 규칙
<br>

##### html에서 스크립트 선언위치

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel = "stylesheet" href = "index.css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <script src="clock.js"></script> <-----------------
</body>
</html>
```
js파일은 항상 body아래에 있어야 된다 제일 마지막에 추가해야된다.

<br>

##### 변수선언 방식

선언방식은 총 3가지가 있다.
* let 
* var
* const

let은 변수가 선언된 블록, 구문 또는 표현식 내에서만 유효한 변수이고 var은 블록범위를 무시하고 전역변수나 함수 지역변수로 선언된다.
const는 상수로 선언한다.

여기서 모든 언어에 통용되는 규칙이 있는데 변수 선언시 상수로 선언하는 것이다.
의도치 않은 [side-effect](https://ko.wikipedia.org/wiki/%EB%B6%80%EC%9E%91%EC%9A%A9_(%EC%BB%B4%ED%93%A8%ED%84%B0_%EA%B3%BC%ED%95%99))를 방지할 수 있으며 필요에 따라 mutable하게 바꾸면 된다.

<br>

##### 데이터를 모아놓는 법
1. Array <br>
	``` const daysOfWeek = [](브라켓) ```
2. Object <br>
	``` 
    const hwanInfo = {
        이름 : 내용,
        age : 32,
        gender : 'male'
    }; (컬리 브라켓) .(콤마)를 통해서 벨류에 접근가능하다 
    ```
> object선언시 JS는 알아서 타입 변환을 해주기 때문에 parameter에 타입없이 이름과 내용만 넣어주면 된다. <br> 세미콜론은 취향따라 알아서 하면된다.

<br>

##### 출력의 두가지 방법 
1. ‘’ “” <br>
이렇게 쓰면 변수를 넣어줄 때 매번 콤마(,)를 적어주거나 concat(+)를 해줘야 하기 때문에 불편하다 <br>
```
function sayHello(potato){
 console.log('hello', potato);
}
```

2. ``  
코틀린에서 이 방식을 채용해서 그냥 “”사이에 쓸 수 있도록 만들었지만 원조는 자바 스크립트다 (아마도?)
```
function sayHello(name, age){
 console.log(`Hello ${name} you are ${age} years old`);
}
```

<br>

##### 가장 기본적인 JS의 Function과 value선언, assingment

* Fucntion
```
function sayHello(name, age){
    return (`Hello ${name} you are ${age} years old`);
}
```
* value, assingment
```
const myInfo = sayHello("박상환", 25, "그린빌");
```
* 호출
```
console.log(myInfo)
``` 

* Object 안에서 function 선언하는 방법

```
const calculator = {
 plus: function(a, b){
   return a+b;
 }, 
 
  min: function(a, b){
   return a-b;
 }
}
const puls = calculator.plus(2, 4)
console.log(puls)
```
> 만약 오류가 난다면 원소를 구분해주는 콤마일 확률이 높다.

<br>

##### 비교 및 선택자 

* 비교연산자<br>
== '값'을 비교 (Equal Operator) <br>
=== '값'과 '타입'을 비교 (Strict Equal Operator)

* null과 undefined<br>
null은 값이 없음을 명시적으로 표시한 것이고 undefined는 그냥 값이 없는 상태이기 때문에 둘을 비교하게 되면 ==는 true가 뜨지만 ===는 false가 뜬다.

>실무에서는 ===를 더 강하게 추천하니 참고

* 선택자
1. 아이디 선택자 : '#'  특정한 id속성이 있는 문서 객체를 선택
2. 클래스 선택자 : '.'  특정한 class속성이 있는 문서 객체를 선택

> 자바스크립트 참조문서를 보고싶다면 [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript)이나 [devdocs](https://devdocs.io/javascript/)에 가면 된다.

<br>

##### DOM(Document Object Model)

자바 스크립트의 DOM(Document Object Model) HTML문서를 마치 객체처럼 가져와서 사용하는 모델이다. <br>
>매우 강력한 개념!!(개념 HTML 또는 XML의 프로그래밍 interface)


JS에서 document.getElementById() 를 쓰면 HTML에 있는 원소를 id값으로 가져올 수 있다. <br>
자매품으로 querySelector()도 있다.<br>
여기서 [document](http://tcpschool.com/javascript/js_dom_document)란 해당 페이지, JS가 호출된 해당 페이지를 의미한다.<br>

> 사용할 때 Unable to set property 'innerHTML' of undefined or null reference 오류메시지가 나온다면 html에 id나 class를 선언했는지 확인!

아래의 코드에서 Unable to set property 'innerHTML' of undefined or null reference 가 나온다.<br>
왜 이런 오류가 발생했을까??  
```
### html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Something</title>
</head>
<body>
    <h1>"Hi!!" </h1>
    <script src = "index.js"></script>
</body>
</html>

### JS
const t = document.getElementById("title"); 
t.style.color = 'red';

if(t != null && t != undefined){
    t.innerHTML = "by";
    console.log(t);
}
```
위 코드를 보면 그 어디에도 title이란 id값이 없기 때문에 나오는 오류다. head에 있는 title은 id값이 아니라 구글로 치면 탭의 이름을 정해주는 "태그"이기 때문이다,<br> 따라서 아래와 같이 수정하면 된다.
```
<h1 id = "title">"Hi!!" </h1>
```

<br>

##### 이벤트

자바스크립트의 존재이유라고 할 만큼 중요하다

```
const title = document.querySelector("#title");

function handleResize(){
    console.log("I have been resized");
}

window.addEventListener("resize", handleResize());
```
addEventListener 에서 handleResize를 어떻게 적냐에 따라 호출되는 시기가 달라진다. 위의 코드처럼 handleResize에 ()중괄호를 적어주면 '지금 당장 호출' 이라는 의미를 가지게 되고 Event가 발생하지 않아도 호출된다.
handleResize에 중괄호를 적지 않으면 내가 원할 때 호출 할 수 있는 EventListener에 적합하게 된다


>매우매우매우매우매우매우 중요한 차이니 잘 알아둬야 한다.


그리고 자바 스크립트는 자동적으로 함수에 객체를 붙이는데 이걸 다룰 준비만 해주면 이벤트가 발생할 때 마다 handleResize에 event 객체를 parameter로 넘긴다
```
function handleResize(event){
    console.log(event);
}

window.addEventListener("resize", handleResize );
```

<br>

##### 간단한 코드
```
const title = document.getElementById("title");

const CLICKED_CLASS = "clicked"; //같은 패키지 아닐경우 불러오기 가능

function handleClick(){
    /*
    const hasClass = title.classList.contains(CLICKED_CLASS)
    if(hasClass){
        title.classList.remove(CLICKED_CLASS);
    }else{
        title.classList.add(CLICKED_CLASS);
    }
    
    toggle함수를 이용해서 위를 간단히 해보자
    */
   title.classList.toggle(CLICKED_CLASS);
}

function init(){
    title.addEventListener("click", handleClick);
}

init();
```
MDN과 JS doc를 이용하면 모르는 함수라도 깔끔하게 쓸 수 있다.<br>
강의가 보고싶다면 [노마드코더](https://nomadcoders.co/javascript-for-beginners)의 바닐라 JS강의를 추천한다.<br>
