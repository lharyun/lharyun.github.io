---
layout: single
title: "Javscript정리"
categories: Javascript
tag: [Javascript]
---

## React 정리 





#### "=="와 "==="의 차이점

<hr/ >

"==" 연산자는 타입 변환이 필요한 경우 타입 변환을 한 후에 동등한지 비교합니다. '==='연산자는 타입 변환을 하지 않으므로 두 값이 같은 타입이 아닌 경우 '==='는 false를 반환합니다.





#### ES6 기준 Javascript의 데이터 타입이 무엇이 있는가?

<hr/ >

boolean, number, string, undefined, null, object, symbol이 있습니다.







#### undefined과 null의 차이에 대해

<hr/ >

undefined는 변수를 선언했지만 값이 할당되지 않은 변수입니다. null은 명시적으로 할당한 것입니다. 그것은 값을 나타내지는 않지만 명시적으로 할당했다는 점에서 undefined와 다릅니다.





#### 호이스팅에 대해 설명해주세요.

<hr/ >

var 키워드로 선언되거나 초기화된 변수는 현재 스코프의 최상위까지 옮겨집니다. 이것을 호이스팅이라고 부릅니다. 선언문만 호이스팅되며 할당(있는 경우)은 호이스팅이 되지 않습니다.





#### var, let, const에 대해 설명해주세요.

<hr/ >

var 로 선언된 변수는 함수 스코프로 작용하고 let, const로 선언된 변수는 블록 스코프로 작용합니다.

var는 호이스팅이 되지만 let과 const는 호이스팅이 되지 않습니다.

또한 var는 재할당, 재선언 모두 가능하지만, let은 재할당만 가능하며 재선언은 불가능 하고 const는 모두 불가능합니다.





#### Javascript에서 this에 동작에 대해 설명해주세요.

<hr/ >

객체 매소드를 호출할때 그 매소드 안에서의 this는 객체 자신입니다.

함수를 호출할 때 함수 내부에서 this는 전역객체, 즉 브라우저에서 window입니다. 

엄격모드('use strict')일 경우 this는 undefined입니다.







