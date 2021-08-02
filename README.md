# Front-End Coding Convention

#### 들여쓰기
- 들여쓰기는 공백문자2개를 사용 (vs code의 설정에서 tap키 공백문자 조절가능)

#### 문장 종료
- 문장의 종료 시 반드시 세미콜론(;)을 사용

#### 폴더/파일
- 폴더/파일 이름은 영문 소문자 camelCase로 작성

#### 컴포넌트
- 컴포넌트는 PascalCase로 명명

#### 변수
- camelCase를 이용하여 변수/함수를 명명
- 예약어를 사용하지 않음
```js
// bad
let import;
let export;
let switch;
let case;
let super;
```
- 범용적인 대문자 약어(ex: HTML, XML, URL)등 사용할 때는 대문자 그대로 사용 가능
```js
let sampleHTML;
let sampleXML;
let sampleYML;
```
- 값이 변하지 않는 변수는 const를 사용, 값이 변하는 변수는 let을 사용.
- 기본적으로 var를 사용하지 않도록 함.
- const를 let보다 위에 사용. (코드 정리)
- const, let은 TDZ가 적용되므로 선언과 할당을 동시에 함.
- 자기 참조 할당을 하지 않도록 함.
```js
// bad
a = a;
{ a, b } = { a, b };
[a, b] = [a, b];
```

#### 전역 변수
- 전역 변수는 사용하지 않도록 함.
```
JS는 전역 변수에 기반을 두며, 모든 컴파일 단위는 하나의 공용 전역 객체(window)에 로딩.
프로그램의 모든 부분에서 접근이 가능하지만 프로그램의 모든 부분에서 변경될 수 있고, 프로그램에 
치명적인 오류를 발생할 여지가 있음.
```
- 암묵적 전역변수를 사용하지 않음.

#### 모듈
- 외부 모듈, 내부 모듈은 시각적으로 구분이 가능하도록 사용.
- 선언 사이 공백을 두는 등의 정리.
- 경로는 작은따옴표로 표시.
- import와 export 키워드를 이용하여 모듈을 로드.
```js
import react, { useState, useEffect } from 'react'
import $ from 'jquery';
import { handlebars } from 'handlebars';
import { throttle } from 'lodash';

import component1 from '../component/component1';
import container1 from '../container/container1';
```

#### 배열과 객체
- 배열과 객체는 리터럴로 선언.
- 리터럴 표기법은 생성자 함수보다 짧고 간결.
```js
// bad
const sampleArray = new Array(1, 2, 3, 4, 5); 
// good
const sampleArray = [1, 2, 3, 4, 5];

// bad
const sampleObject = new Object();
// good
const sampleObject = {};
```

#### 배열
- 배열 요소 중 줄바꿈을 한다면 모든 요소의 줄바꿈을 함.
```js
// bad
const sampleArray = [
  1, 2, 3,
  4,
  5
]

// good
const sampleArray = [
  1,
  2,
  3,
  4,
  5
];
```

#### 객체
- 객체의 요소가 1개일 경우 한줄 정의를 허용.
- 객체의 요소가 2개 이상일 경우 개행.
```js
// bad
const sampleObject = {foo: 'a', val: 'b'};

// good
const sampleObject = {foo: 'a'};
const sampleObject = {
  foo: 'a',
  var: 'b'
};
```
- 객체 정의 시 콜론 (:) 앞의 공백은 제거하고 뒤의 공백은 강제.
```js
// bad
const sampleObject = {
  foo : 'a'
}

//good
const sampleObject = {
  foo: 'a'
}
```
#### 함수
- 함수 내 return은 한번만 사용한다. (예외 처리로 빠져나갈 필요가 있는 경우는 제외)
```js
// bad
function sampleFunction() {
  let retVal = '';

  // ...

  if (condition) {
    return condition;
  }

  // ...

  return retVal;
}

// good
function sampleFunction() {
  let retVal = '';

  // ...

  if (condition) {
    retVal = condition
  }
  
  // ...

  return retVal
}
```

#### 일반함수
- 함수 생성자를 사용하지 않도록 함. 문자열로 전달되는 파라미터가 수행 시점 eval함수로 처리됨.
- eval함수에 대한 MDN의 설명
```
eval()은 인자로 받은 코드를 caller의 권한으로 수행하는 위험한 함수입니다. 악의적인 영향을 받았을 수 있는 문자열을 eval()로 실행한다면, 당신의 웹페이지나 확장 프로그램의 권한으로 사용자의 기기에서 악의적인 코드를 수행하는 결과를 초래할 수 있습니다. 또한, 제3자 코드가 eval()이 호출된 위치의 스코프를 볼 수 있으며, 이를 이용해 비슷한 함수인 Function으로는 실현할 수 없는 공격이 가능합니다.

또한 최신 JS 엔진에서 여러 코드 구조를 최적화하는 것과 달리 eval()은 JS 인터프리터를 사용해야 하기 때문에 다른 대안들보다 느립니다.

추가로, 최신 JavaScript 인터프리터는 자바스크립트를 기계 코드로 변환합니다. 즉, 변수명의 개념이 완전히 없어집니다. 그러나 eval을 사용하면 브라우저는 기계 코드에 해당 변수가 있는지 확인하고 값을 대입하기 위해 길고 무거운 변수명 검색을 수행해야 합니다. 또한 eval()을 통해 자료형 변경 등 변수에 변화가 일어날 수 있으며, 브라우저는 이에 대응하기 위해 기계 코드를 재작성해야 합니다. 그러나, (다행히) window.Function이라는 eval보다 훨씬 나은 대안이 있습니다. eval()을 사용하는 코드를 Function()으로 바꾸는 방법에 대해서는 아래를 참조하세요.
```
```js
// bad
let add = new Function("a", "b", "return a + b");

//good
let add = function(a, b) {
  return a + b;
}
```
- 함수는 사용 이전의 위치에서 선언.
```js
function add(a, b) {
  return a + b;
}
const sampleFunc = add(1, 2);
```
- 함수 선언문은 변수 선언문 다음에 오도록함.
- block scope에서는 함수를 선언하지 않는다.
```js
// bad
if (condition) {
  function sampleFunction() {
    //...
  }
} else {
  function sampleFunction() {
    //...
  }
}

//good
let sampleFunction;
if (condition) {
  sampleFunction = function() {
    // ...
  }
} else {
  sampleFunction = function() {
    // ...
  }
}
```

#### 화살표 함수
- 함수 표현식 대신 화살표 함수를 사용.
```js
const sampleArray = [1, 2, 3, 4, 5];

// bad
const hap = sampleArray.map(function (unit) {
  return unit + unit;
});

// good
const hap = sampleArray.map(unit => {
  return unit + unit;
});
```
- 함수 내용의 내용이 하나만 있다면 중괄호 생략이 가능.
- 중괄호를 생략할 경우 암시적 반환 가능. 그 외 return을 명시.
- 암시적 반환을 사용할 경우 함수 본문 전 개행X, 소괄호를 사용할 경우 개행 가능
```js
const sampleArray = [1, 2, 3, 4, 5];

// bad
const hap = sampleArray.map(unit => 
  unit + unit
);

// good
const hap = sampleArray.map(unit => unit + unit);
const hap = sampleArray.map(unit => (
  unit + unit
));
```

#### 주석
- 설명 대상과 동일한 들여쓰기.
```js
function add(a, b) {  
  // 덧셈 연산
  return a + b;
}
```
- 문장 끝에 주석을 작성할 경우 한줄 주석을 사용하여 주석 표시 전후 공백을 추가.
```js
function add(a, b) {
  return a + b; // 덧셈 연산
}
```
- 여러줄 주석을 사용할 경우 "/** */"를 사용하며, 각 문장 가장 앞에 " * "를 표시.
- 주석의 닫는 부분인 "*/"는 한칸 띄우고 표현.
```js
/**
 * 뎃셈 연산
 * comment1...
 * comment2...
 */
function add(a, b) {
  return a + b;
}
```

#### Promise
- Promise 생성자 함수에는 async함수를 사용하지 않도록 함.
- 코드가 복잡해지고 오류를 잡기 힘듬.
```js
// bad
const sampleFunction = new Promise(async (a, b) => {
  // ...
});
```

#### 문자열
- 작은 따옴표로 문자열 선언
- 문자열 내 작은 따옴표가 포함될 경우 템플릿 리터럴(backtick)을 사용.
```js
// bad
const val = "string";

// good
const val = 'string';

// bad
const dStr = 'this is ' + val;

// good
const dStr = `this is ${val}`;
```

#### 조건문
- 한줄 block이더라도 중괄호를 생략하지 않도록 함.
- 명확한 표현을 위해 줄바꿈을 사용.
```js
// bad
if (condition) sample1();
else sample2();

// good
if (condition) {
  // ...
} else {
  // ...
}
```
- 조건문 키워드 사이에 공백문자를 한칸 둠.
```js
// bad
if(condition){
  // ...
}

// good
if (condition) {
  // ...
}

//bad
for(let i = 0; i < 100; i++){
  // ...
}

//good
for (let i = 0; i < 100; i++) {
  // ...
}
```
- 비교 연산자 중 equal은 == 대신 === 를 사용하여 표현.
```js
// bad
if (a == b) {
  // ...
}

// good
if (a === b) {
  // ...
}
```

#### 공백
- 키워드, 연산자와 다른 코드 사이에 공백.
- 괄호의 시작후와 종료전에 공백X.
```js
// bad
if(condition){
  // ...
}

// bad
if ( condition ) {
  // ...
}

// good
if (condition) {
  // ...
}
```
- 콤마 다음에 공백을 추가.
```js
// bad
const sampleArray = [1,2,3,4,5];

// good
const sampleArray = [1, 2, 3, 4, 5];
```