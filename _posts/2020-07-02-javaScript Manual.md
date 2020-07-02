---
layout: post
title:  "JavaScript 간편 정리"
author: hwan
categories: [ JavaScript ]
tags: [ 진행중 ]
image: assets/images/JavaScript.jpg
description: ""
rating: ""
---
자바 스크립트 = 웹에 쓰이는 하나뿐인 프로그래밍 언어  => 옵션이 하나뿐이기 때문에 웹안에 웹만들거나 interactive하게 만들고 싶을 때 사용
프론트의 필수언어
장점 : Fragmentation(분열) 이 없다. 모두가 알기 때문에
단점 : 막혀있다.

이거 배우면 개섹시한 웹사이트 만들 수 있음

매우 interactive 하다


ES5, ES6... 자바스크림트 버전 Specification(설명서) 이런거 다 때려치우고 우린 최신걸 배운다. 
우리는 바닐라 자바스크립트한다. 라이브러리 없는 순수 자바 스크립트

바닐라 자바스크립트를 배운다는것은 웹의 원초를 배운다는 것, 복잡하고 귀찮지만 강력하다

js파일은 항상 body아래에 있어야 된다 제일 마지막에 추가해야된다.

자바스크립트는 훈육하지않는 아빠같다 단지 이해만 하고 고쳐주려고 하진 않는다. <- 이게 개같은점

JS에서 let는 지역변수를 의미, 변수가 선언된 블록, 구문 또는 표현식 내에서만 유효한 변수를 선언
var과 차이점은 블록범위를 무시하지 않고 젼역변수나 함수지역변수로 선언되지 않는점

const 상수로 선언함 static final or val

모든 언어에 통용되는 규칙 !!!! : valueable 선언시 const 또는 val 로 선언할 것!!
타입 : String, Number, Boolean, Float ....

데이터를 모아놓는 법 : 
1. Array 
	const daysOfWeek = [](브라켓)
2. Object
	 const hwanInfo = {}(컬리 브라켓) .(콤마)를 통해서 벨류에 접근가능하다

함수는 함수
함수 선언 방법 (parameter에 부가적인 선언 없이 이름만 넣으면 된다) 자바스크립트는 타입이 없어 -> 정확히는 알아서 타입 캐스팅을 해줌

-출력의 두가지 방법 
‘’ “”를 쓰는것 
이렇게 쓰면 변수를 넣어줄 때 매번 콤마(,)를 적어주거나 concat(+)를 해줘야 하기 때문에 불~편
function sayHello(potato){
 console.log('hello', potato);
}
 
`` 백코트 쓰는방식 -> 코틀린에서 이 방식을 채용해서 그냥 “”사이에 쓸 수 있도록 만들었지만 원조는 자바 스크립트다 원조국밥 지린다.
function sayHello(name, age){
 console.log(`Hello ${name} you are ${age} years old`);
}


가장 기본적인 JS의 Function과 value선언, assingment
function sayHello(name, age){
 return (`Hello ${name} you are ${age} years old`);
}
 
const myInfo = sayHello("박상환", 25, "그린빌");
 
console.log(myInfo)
 
(중요)Object 안에서 function 선언하는 방법
 
const calculator = {
 plus: function(a, b){
   return a+b;
 }, <- 매우 존나게 중요 / 실수 자주 일어날 가능성이 높다
 
  min: function(a, b){
   return a-b;
 }
}
const puls = calculator.plus(2, 4)
console.log(puls)
JS에서 document.getElementById() 를 쓰면 HTML에 있는 원소를 id값으로 가져올 수 있다. 
여기서 document란 해당 페이지, JS가 호출된 해당 페이지를 의미한다.

자바 스크립트의 DOM(Document Object Model) HTML문서를 마치 객체처럼 가져와서 사용하는 모델 강력!!  (개념 HTML 또는 XML의 프로그래밍 interface)

document.getElementById("title").innerHTML = "by" 에서  Unable to set property 'innerHTML' of undefined or null reference 가 나온다
왜 이런 오류가 발생했을까??  
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

위 코드를 보면 그 어디에도 title이란 id값이 없기 때문에 나오는 오류다. head에 있는 title은 id값이 아니라 구글로 치면 탭의 이름을 정해주는 "태그"이기 때문이다

수정 : <h1 id = "title">"Hi!!" </h1>

DOM 
document내부 원소의 id를 통해 참조가 가능하고
ex) document.getElementById("title")

document자체적으로 참조도 가능하다 
ex) document.title = "by"

JS는 이벤트를 위해 만들어 졌다.
-----------------------------------------------------
const title = document.querySelector("#title");

function handleResize(){
    console.log("I have been resized");
}

window.addEventListener("resize", handleResize());

코드에서 handleResize를 어떻게 적냐에 따라 호출되는 시기가 달라진다. 위의 코드처럼 handleResize에 ()중괄호를 적어주면 '지금 당장 호출' 이라는 의미를 가지게 되고 Event가 발생하지 않아도 호출된다.
handleResize에 중괄호를 적지 않으면 내가 원할 때 호출 할 수 있는 EventListener에 적합하게 된다

매우매우매우매우매우매우 중요한 차이니 잘 알아둬야 한다.

function handleResize(event){
    console.log(event);
}

window.addEventListener("resize", handleResize );

그리고 자바 스크립트는 자동적으로 함수에 객체를 붙이는데 이걸 다룰 준비만 해주면 이벤트가 발생할 때 마다 handleResize에 event 객체를 parameter로 넘긴다

비교 연산자 
== '값'을 비교 (Equal Operator) 
=== '값'과 '타입'을 비교 (Strict Equal Operator)

null 과 undefined의 차이
null은 값이 없음을 명시적으로 표시한 것이고 undefined는 그냥 값이 없는 상태이기 때문에 둘을 비교하게 되면 ==는 true가 뜨지만 ===는 false가 뜬다.

실무에서는 ===를 더 강하게 추천하니 참고

JS의 선택자를 알아보자 
1. 아이디 선택자 : #  특정한 id속성이 있는 문서 객체를 선택
2. 클래스 선택자 : .  특정한 class속성이 있는 문서 객체를 선택

event의 근원을 찾고싶다면 MDN을 찾으면 된다
----------------------------------------------------------------------
타이틀의 function 을 이용한 간단한 코드
const title = document.getElementById("title");

const CLICKED_CLASS = "clicked"; //같은 패키지 안일경우 불러오기 가능

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

MDN과 JS doc를 이용하면 모르는 함수라도 깔끔하게 쓸 수 있다.