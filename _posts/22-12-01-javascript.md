---
title: "자바스크립트 개념 공부"
categories:
 - javascript
tags: [javascript] 
toc: true
author_profile: true #profile sidebar 감추기
# sidebar:
#     nav: "docs" # 목차 사이드바
search: true #검색 피하기
---



[toc]



#### 변수

1. let : 바꿀 수 있는 값
2. const : 바뀌지 않는 값



##### 변수명 규칙

1. 문자와 숫자, $, _ 만 사용.
2. 첫글자는 숫자가 될 수 없다.
3. 예약어는 사용할 수 없다.
4. 가급적 상수는 대문자로 사용할 것.
5. 변수명은 읽기 쉽고 이해할 수 있게 선언.



#### 자료형

1. 문자형 :  "", '', \`${}`
2. 숫자형
3. Boolean : true,false
4. null, undefined



###### typeof 연산자

자료형을 알 수 있다.



#### 형변환

1. String() : 괄호 안에 값을 문자형으로
2. Number() : 숫자형으로, true -> 1, false,빈문자열,null,undefined,NaN -> 0
3. Boolean() : 0, "", null, undefined, NaN -> false



#### 연산자

거듭제곱 : ** -> ex) 2 ** 3 -> 8



#### 함수(function) -> 함수 선언문 : 어디서든 호출 가능

```javascript
function sayHello(name){
    let msg = "hello";
    if(name){
        msg += `, ${name}`;
    }
    console.log(msg);
}
sayHello(); // "hello" -> 자바와는 다르게 인자에 아무것도 안써줘도 에러없이 잘 실행된다.
sayHello("이동하"); // hello, 이동하
```



#### 화살표 함수 -> 함수 아래에서만 호출 가능

```javascript
let showError = () => {
	console.log('error');
}

showError();
```



#### 객체(Object)

```javascript
const superman={
    name : 'clark',
    age : 33,
}

// 접근
superman.name
superman['age']

// 추가
superman.gender = 'male';
superman['hairColor'] = 'black';

// 삭제
delete superman.hairColor;

```



#### for in 반복문(보통 객체를 순회할 때 사용)

```javascript
for(let key in superman){
    console.log(key);
}
```



#### 객체-method,this

```javascript
let boy = {
    name : "mike",
    showName : function(){
        // 이 메소드의 this는 해당 객체를 가리킨다.
        console.log(this.name);
    }
}

let boy = {
    name : "mike",
    showName : () => {
        // 이 코드를 실행하면 에러가 난다. 화살표 함수 내에서 this는 전역객체를 의미한다.
        console.log(this);
    }
}

```



#### 배열 : 순서가 있는 리스트

```javascript
// js에서 배열에는 문자, 숫자, 불린값, 객체, 함수를 넣을 수 있다.
let students = ['철수','영희',3,false,{name:'mike',age:30},function(){console.log('TEST')}];

// 배열 맨끝 요소 추가
.push()

// 배열 맨끝 요소 삭제
.pop()

// 배열 맨앞 요소 추가
.unshift()

// 배열 맨앞 요소 삭제
.shift()
```



##### for of 반복문(배열 순회할 때 사용하는 것이 좋다.)

```javascript
let days = ['월','화','수'];

for(let day of days){
	console.log(day)
}
```

