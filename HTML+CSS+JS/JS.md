# JavaScript
- 웹페이지를 동적으로 움직이게 만들어준다.
- HTML이 몸이라면 CSS는 스타일리쉬(화장,옷)이라면 JS는 스마트폰이다. 
- Node js 및 React js등 여러가지 분야로 확장됨

## JavaScript의 기본

### 기본적인 출력

```
console.log("Hello World"); // Hello World
```

### 값(value)와 변수(variable)
- var : 런타임 시 변수의 값에 의해 동적으로 유형이 결정되며 이를 동적 바인딩(Dynamic Binding)이라고 한다.
- 변수에 넣을 수 있는 값은 다양하며 단일 자료형의 값, 표현식, 함수까지 대입이 가능하다.

### 주석(Comment)
- 다른 프로그래밍 언어와 비슷하며 한 줄은 // 블록 단위는 /* */로 표시한다.

### 자료형
- `Number` : var num = 10;
- `String` : var s = "Hello";
- `isTrue` : var bool = true;
- `null` : var empty = null;
- `undefined` : var x;
- `Symbol` : var num = 10; // ES6이후 추가된 변경 불가능한 자료형이며 참조형 키(Key)로 사용이 가능하다.
- `Object` : var person={name:"김철수",age=25}
- `Array` : var nations = ["Korea","China","Japan"]
- `function` : var addNation = function(nation){nations.push(nation);} //함수 선언 및 정의
addNation("USA"); //함수 호출

#### 자료형의 타입
`원시타입` : 
