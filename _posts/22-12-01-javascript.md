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



##### 변수의 종류

1. let : 바꿀 수 있는 값

   변수의 생성과정

   1. 선언 단계
   2. 초기화 단계
   3. 할당 단계
2. const : 바뀌지 않는 값

   변수의 생성과정

   1. 선언 + 초기화 + 할당
3. var : 한번 선언된 변수를 다시 선언할 수 있다.



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
5. Symbol



###### typeof 연산자

자료형을 알 수 있다.



#### 형변환

1. String() : 괄호 안에 값을 문자형으로
2. Number() : 숫자형으로, true -> 1, false,빈문자열,null,undefined,NaN -> 0
3. Boolean() : 0, "", null, undefined, NaN -> false



#### 연산자

거듭제곱 : ** -> ex) 2 ** 3 -> 8



#### Math

- Math.ceil() 올림
- Math.floor() 내림
- Math.round() 반올림



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



##### 화살표 함수 -> 함수 아래에서만 호출 가능

```javascript
let showError = () => {
	console.log('error');
}

showError();
```



##### 생성자 함수

```javascript

function User(name,age){
    // this = {} 함수 본문을 실행하면 빈 객체 생성
    this.name = name;
    this.age = age;
    // return this this를 리턴해준다. 주석처리한 부분은 실제 동작과정이나 실제 코드로
    // 작성하지 않는다.
    
}

// new 연산자로 호출
let user1 = new User('Mike',30);
let user2 = new User('Jane',22);
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



##### Computed Property

```javascript
let a = 'age';

const user = {
    name : 'Mike',
    [a] : 30 //[a]는 변수 a에 할당된 값이 들어간다 따라서 age : 30
}

// 식 자체를 넣는 것도 가능.
const user = {
    [1 + 4] : 5,
    ["안녕"+"하세요"] : "Hello"
}

// user -> {5:5, 안녕하세요:"Hello"}
```



##### Symbol : 유일한 식별자

###### Symbol 생성

```javascript
const a = Symbol(); // new 붙이지 않는다
const b = Symbol();

console.log(a) // Symbol()
console.log(b) // Symbol()

console.log(a == b) // false
```



###### property key : 심볼형

```javascript
const id = Symbol('id');
const user = {
    name : 'Mike',
    age : 30,
    [id] : 'myid'
}

// user -> {name :"Mike", age : 30, Symbol(id) : "myid"}
```



###### Symbol.for() : 전역 심볼

- 하나의 심볼만 보장받을 수 있음
- 없으면 만들고, 있으면 가져오기 때문
- Symbol 함수는 매번 다른 심볼 값을 생성하지만, Symbol.for 메소드는 하나를 생성한 뒤 같은 Symbol을 공유

```javascript
const a = Symbol.for('id');
const b = Symbol.for('id');

// a == b -> true

symbol.keyFor(a); // "id"
```







##### 객체 메소드

1. Object.assign() : 객체 복제

   ```javascript
   const user = {
       name : 'Mike',
       age : 30
   }
   
   // 초기값이 빈 상태에서 user객체 값 복제
   const cloneUser = Object.assign({},user);
   
   // 초기값에 gender 속성값 +  user값 복제
   const cloneUser = Object.assign({gender:'M'},user)
   
   //동일한 키일 경우에는 덮어씌어진다
   const cloneUser = Object.assign({name:'Tom'},user)
   // -> name : 'Mike'
   
   ```

2. Object.keys() : 키 배열 반환

   ```javascript
   const user = {
       name : 'Mike',
       age : 30,
       gender : 'maie',
   }
   
   Object.keys(user); // ["name","age","gender"]
   ```

3. Object.values() : 값 배열 반환

4. Object.entries() : 키/값 배열 반환

   ```javascript
   Object.entries(user); // [["name","Mike"],["age",30],["gender","mail"]]
   ```

5. Object.fromEntries() : 키/값 배열을 객체로 반환

   ```javascript
   const arr = [["name","Mike"],["age",30],["gender","mail"]];
   Object.fromEntries(arr); 
   
   /*
   const user = {
       name : 'Mike',
       age : 30,
       gender : 'maie',
   }
   */
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

//특정 요소 지움 n번 부터 m개 지움
.splice(n,m)

// 특정요소 지우고 추가
.splice(n,m,x)

// n부터 m까지 반환
.slice(n,m)

// 합쳐서 새 배열 반환
.concat(arr2,arr3,...)

// 배열 반복
.forEach(fn)

// 조건에 만족하는 값 반환
.filter(fn)

// 함수를 받아 특정 기능을 실행하고 새로운 배열을 반환
.map(fn)

// 배열 재정렬, 배열 자체가 변경
.sort()

// 합치기
.reduce(fn,초기값)
```



##### for of 반복문(배열 순회할 때 사용하는 것이 좋다.)

```javascript
let days = ['월','화','수'];

for(let day of days){
	console.log(day)
}
```



#### 구조 분해 할당

{: .notice--info}

구조 분해 할당 구문은 배열이나 객체의 속성을 분해해서 그 값을 변수에 담을 수 있게 하는 표현식



```javascript
let [x,y] = [1,2];

console.log(x); // 1
console.log(y); // 2

let users = ['tom','mike','sam'];
let [user1, user2, user3] = users;

console.log(user1); // 'tom'
console.log(user2); // 'mike'
console.log(user3); // 'sam'
```



##### 기본값

```javascript
let [a,b,c] = [1,2]; // c에는 undefined
let [a=3,b=4,c=5] = [1,2]; // 이 코드 처럼 기본값을 미리 지정해줘서 에러 방지
```



##### 일부 반환값 무시

```javascript
let [user1, ,user2] = ['mike','sam','tom','jam','tony'];

console.log(user1); // 'mike'
console.log(user2); // 'tom'
```



##### 객체 구조 분해

```javascript
let user = {name : 'mike', age : 30};
let {name, age} = user;

console.log(name); // 'mike'
console.log(age); // 30
```



#### 나머지 매개변수(...), 전개 구문

js에서 함수 인수의 개수 제한 없다.

```js
function showName(name){
    console.log(name);
}

showName('Mike'); // 'Mike'
showName('Mike','Tom'); // ?
showName(); // undefined
```



##### 나머지 매개변수(정해지지 않은 개수의 인수를 배열로 나타낼 수 있다.)

```js
function showName(...names){
    console.log(names);
}

showName('Mike'); // ['Mike']
showName('Mike','Tom'); // ['Mike','Tom']
showName(); // []
```



##### 전개구문

```javascript
// 배열에서의 활용
let arr1 = [1,2,3];
let arr2 = [4,5,6];

int result = [...arr1,...arr2];

console.log(result); // [1,2,3,4,5,6]

int result2 = [0,...arr1,...arr2,7];
console.log(result2); // [0,1,2,3,4,5,6,7]


// 객체에서의 활용
let user = {name : 'Mike'};
let info = {age : 30};
let fe = ["js","react"];
let lang = ["korean","english"];

user = {
    ...user,
    ...info,
    skills : [...fe,...lang],
};

console.log(user);
//{name : "Mike", age:30, skills:['js','react','korean','english']}

```



#### 클로저

{: .notice--info}

함수와 렉시컬 환경의 조합, 함수가 생성될 당시의 외부 변수를 기억, 생성 이후에도 계속 접근 가능



#### call, apply, bind





