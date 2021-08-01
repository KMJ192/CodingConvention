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



## HTML
