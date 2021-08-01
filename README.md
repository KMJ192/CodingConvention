# Front-End Coding Convention

## javascript / typescript
### 들여쓰기
- 들여쓰기는 공백문자2개를 사용한다. (vs code의 설정에서 tap키 공백문자 조절가능)
- space와 tab을 섞어서 사용하지 않도록 한다.

### 문장 종료
- 문장의 종료 시 반드시 세미콜론(;)을 사용하도록 한다.

### 명명 규칙
- camelCase를 이용하여 변수/함수를 명명한다.
- 컴포넌트는 PascalCase로 명명한다.
- 예약어를 사용하지 않도록 한다.
- 범용적인 대문자 약어(ex: HTML, XML, URL)등 사용할 때는 대문자 그대로 사용한다.
```
parseHTML
parseXML
```

### 전역 변수
- 전역 변수를 사용하지 않는다.
- JS는 전역 변수에 기반을 두며, 모든 컴파일 단위는 하나의 공용 전역 객체(window)에 로딩된다.
  프로그램의 모든 부분에서 접근이 가능하지만 프로그램의 모든 부분에서 변경될 수 있고, 프로그램에 
  치명적인 오류를 발생할 여지가 생긴다.
- 암묵적 전역변수를 사용하지 않는다.

### 변수
- 값이 변하지 않는 변수는 const를 사용, 값이 변하는 변수는 let을 사용한다.
- 기본적으로 var를 사용하지 않도록 한다.
- const를 let보다 위에 사용한다. (코드 정리)
- const, let은 TDZ가 적용되므로 선언과 할당을 동시에 한다.
- 자기 참조 할당을 하지 않도록 한다.
```js
a = a;
{ a, b } = { a, b };
[a, b] = [a, b];
```

### 모듈
- 외부 모듈, 내부 모듈은 시각적으로 구분이 가능하도록 사용한다.
- 선언 사이 공백을 두는 등의 정리
```js
import react, { useState, useEffect } from 'react'
import $ from 'jquery';
import { handlebars } from 'handlebars';
import { throttle } from 'lodash';

import component1 from '../component/component1';
import container1 from '../container/container1';
```

### 배열과 객체
- 배열과 객체는 반드시 리터럴로 선언한다.
- 리터럴 표기법은 생성자 함수보다 짧고 간결하다.
```js
const sampleArray = new Array(1, 2, 3, 4, 5);  // X
const sampleArray = [1, 2, 3, 4, 5]; // O

const sampleObject = new Object(); // X
const sampleObject = {}; // O
```
#### 배열
- 배열 복사 시 for loop를 사용하지 않고, spread 연산자를 사용한다.
```js
const sampleArray = [1, 2, 3, 4, 5];
const cloneArray = [...sampleArray];
```
- 배열 요소 중 줄바꿈을 한다면 모든 요소의 줄바꿈을 한다.
```js
const sampleArray = [
  1,
  2,
  3,
  4,
  5
];
```

#### 객체
- 객체의 요소가 1개일 경우 한줄 정의를 허용한다.
- 객체의 요소가 2개 이상일 경우 개행한다.
- 객체 정의 시 콜론 (:) 앞의 공백은 제거하고 뒤의 공백은 강제한다.
```js
const sampleObject = {foo: 'a'};
const sampleObject = {
  foo: 'a',
  varL 'b'
};
```

### 함수
#### 일반함수
- 함수 생성자를 사용하지 않는다. (문자열로 전달되는 파라미터가 수행 시점 eval로 처리되어 속도가 느려짐)
- 함수는 사용 이전의 위치에서 선언한다.
- 함수 선언문은 변수 선언문 다음에 오도록한다.
```js
function add(a, b){
  return a + b;
}
const sampleFunc = add(1, 2);
```
- block scope에서는 함수를 선언하지 않는다.
#### 화살표 함수
- 함수 표현식 대신 일반 함수를 사용하도록 한다.
```js
const sampleArray = [1, 2, 3, 4, 5];
const hap = sampleArray.map(unit => {
    return unit + unit;
});
```

### 주석
- 설명 대상과 동일한 들여쓰기한다.
```js
function add(a, b){  
  // 덧셈 연산
  return a + b;
}
```
- 문장 끝에 주석을 작성할 경우 한줄 주석을 사용하여 주석 표시 전후 공백을 추가한다.
```js
function add(a, b){
  return a + b; // 덧셈 연산
}
```
- 여러줄 주석을 사용할 경우 "/** */"를 사용하며, 각 문장에 " * "를 표시한다.
- */는 한칸 띄우고 표현한다.
```js
/**
 * 뎃셈 연산
 * comment1...
 * comment2...
 */
function add(a, b){
  return a + b;
}
```
## HTML
