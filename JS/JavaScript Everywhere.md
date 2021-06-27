
# Hello World
```
const express = require('express');
const app = express();

app.get('/',(req,res)=>res.send('Hello World'));
app.listen(4000,()=> console.log('Listening on port 4000'));
```

## Nodemon
- 서버 어플리케이션의 코드가 변경되면 웹 서버를 새로 시작해야 한다.
- nodemon을 이용하면 서버를 자동으로 재시작할 수 있다.
- package.json 파일 내의 scripts 명령어를 변경하여 사용한다.
- npm run dev로 실행
// package.json
```
"scripts":{
    ...
    "dev" : "nodemon src/index.js"
    ...
}
```

### 값(value)와 변수(variable)
- var : 런타임 시 변수의 값에 의해 동적으로 유형이 결정되며 이를 동적 바인딩(Dynamic Binding)이라고 한다.
- 변수에 넣을 수 있는 값은 다양하며 단일 자료형의 값, 표현식, 함수까지 대입이 가능하다.

### 주석(Comment)
- 다른 프로그래밍 언어와 비슷하며 한 줄은 // 블록 단위는 /* */로 표시한다.

### 자료형
- `Number` : var num = 10;
- `String` : var s = "Hello";
- `Boolean` : var bool = true;
- `null` : var empty = null;
- `undefined` : var x;
- `Symbol` : var num = 10; // ES6이후 추가된 변경 불가능한 자료형이며 참조형 키(Key)로 사용이 가능하다.
- `Object` : var person={name:"김철수",age=25}
- `Array` : var nations = ["Korea","China","Japan"]
- `function` : var addNation = function(nation){nations.push(nation);} //함수 선언 및 정의
addNation("USA"); //함수 호출

#### 자료형의 타입
- `원시타입(Primitive Data Type)` : `Number` `String` `Boolean` `null` `undefined` `Symbol`
- `참조타입(Reference Data Type)` : `Object` `Array` `function`

### 조건문
- `switch` : case의 값과 일치 여부를 확인하며 === 연산자(값과 자료형을 모두 비교)를 사용한다. 

```
switch(표현식){
    case 값1:
        명령문1;
        break;
     case 값2:
        명령문2;
        break;
     default:
        명령문3;
}
```

### 반복문
- `for in` : for(속성명 in 반복 대상)으로 구성되며 반복문을 통해 요소를 한개씩 가져와 속성명으로 선언과 동시에 할당한다.

```
var nations = ["Korea","China","Japan"]

for(var item in nations){
    console.log(item); // Korea China Japan
}
```

### 숫자형
- `Infinity` : 무한대를 의미한다. `Infinity`로 나누면 무슨 값이든 0이 된다.
- `Nan` : Not a number 유요하지 않는 값 or 숫자가 너무 커서 표현할 수 없을때 표현된다.

### null 과 undefined
- `null` : 비어 있는, 존재하지 않는 값 `typeof`로 자료형을 확일할 때 `object`를 반환하는데 이는 JS 기존 이슈로 인한 결과이다.
- `undefined` : 아무 값도 할당받지 않은 상태 변수에 어떠한 값도 대입하지 않거나 함수에서 명시적으로 값을 반환하지 않았을 때 `undefined`로 반환
```
var value=null;
console.log(value); // null
console.log(typeof value); // object

var value;
console.log(value); // null
console.log(typeof value); // object
```

### 템플릿 문자열
- `${value}` : ``(억음 부호)표시를 사용하며 계산된 결과가 문자열로 변경되어 삽입된다.
```
var PI=3.141592
console.log(`PI의 값은 ${PI}입니다.`) // PI의 값은 3.141592입니다.
```

### 산술 연산자
- `**` : 거듭제곱 연산자

### 비교 연산자
- `==`(동등 연산자) : 비교 대상값의 자료형이 서로 다르면 강제로 형을 바꾼 뒤 비교
- `===`(일치 연산자) : 값을 비교뿐 아니라 자료형까지 일치하는지 비교

### 논리 연산자
- `!!` : not 연산자에 not 연산자를 부여한다.

### 객체(Object)
- 객체란 값들을 그룹으로 묶은 데이터 모음이다.
- 객체를 만드는 방법은 표현식으로 `{}`를 소용한다.
- 키(key)와값(value)를 한 쌍으로 정의하며 속성(Properties)라 부른다.

#### 🏆JSON(JavaScript Object Notation)🏆
- JS의 객체와 매우 유사한 구조를 지닌 데이터 교환 형식이다.
- JSON 형태는 key : value로 구성되어 있다.

```
var person={
    name: "김철수",
    age : 25,
    tour : ["중국","일본","미국","영국","캐나다"],
    addTour : function(nation){
        this.tour.push(nation);
    }
}

person.addTour("덴마크");
console.log(person.tour) // 중국 일본 미국 영국 캐나다
```
### arguments객체
- 매개변수와 달리 함수가 호출될 때 전될되는 값이다.
- 매개변수의 개수가 달라도 에러를 발생하지 않는다.

```
function sum() {
  var total = 0;
  for (var i = 0; i < arguments.length; i++) {
    total += arguments[i];
  }
  console.log(arguments instanceof Array);
  return total;
  ```
### 나머지 매개변수
- ES6에서 추가된것으로 arguments 객체는 모든 인자를 전달하는 반면 ...restParameter(나머지 매개변수)는 할당하지 않는 나머지 변수를 의미한다.
```
function sum(num1,num2,...restParameter){ // num1 = 1, num2 =2, restParameter=[3,4,5]
var total = 0;
  for (var i = 0; i < arguments.length; i++) {
    total += arguments[i];
  }
  console.log(arguments instanceof Array);
  return total;
}
sum(1,2,3,4,5);
```

### 함수 호이스팅
- JS에서 함수를 선언하기 전에 호출이 가능하다.
```
hello();
function hello() {
  console.log("Hello World");
}
```

### let
- 변수의 유효범위를 블록 범위로 지정한다.
```
if(true){
  var functionScopeValue = 'global';
  let blockScopeVale = 'local';
}

console.log(functionScopeValue); // global
console.log(blockScopeVale); // ReferenceError
```

### 객체 속성 기술자(Property Descriptor)
- JS의 모든 객체 속성은 자기 자신에 대한 정보를 담고 있는 속성 기술자를 가지고 있다.
- Object.getOwnPropertyDescriptor() 사용하여 기술자 객체를 가져온다.
- Object.defineProperty를 통해 해당 객체의 속성을 가져온다
    + `value` : 값을 나타낸다.
    + `enumerable` : 속성을 나열 가능 여부를 나타낸다.
    + `writable` : 값의 변경 여부를 나타낸다.
    + `configurable` : 속성 기술자 변경 여부를 나타낸다.

### Class
- 생성자는 constructor()을 이용하고 상속은 extends를 이용한다.
- 나머지는 다른 프로그래밍 언어와 비슷하다.

### Module(모듈)
- `export` : 모듈 내의 특정 코드를 외부에서 사용이 가능하게 만든다.
- `import` : export 한 코드들을 가지고 올 수 있다.
- `default` : 모듈에서 기본으로 내보내는 값을 말한다.
- `as` : 현재 모듈에서 다른 이름으로 변경이 가능하다.
- 런타임 로딩(Runtime Loading) : 의존 관계가 형성된 모듈들을 어플리케이션이 구동 시점에 비동기 HTTP 요청으로 불러드려 실행한다.
- 번들링(Bundling) : 의존 관계가 형성된 모듈들을 하나의 파일로 묶어준다. 어플리케이션이 구동할 때 묶어진 파일을 업로딩 하며 대표적 모듈 번들러로는(Webpack)이 있다.

### 표준 내장 객체
- Number.isNaN(value) : value가 Nan이면 true 그렇지 않으면 false
- Number.isInteger(value) : value가 정수면 true 그렇지 않으면 flase
- Array.isArray(value) : value가  배열이면 true 그렇지 않으면 flase
- ParseInt(value) : value(문자열)을 정수로 변환한다.
- ParseFloat(value) : value(문자열)을 실수로 변환한다.
- slice(s,e) : s부터 e까지 자른다.(e는 필수사항은 e가 없을시 인덱스 끝까지 자른다. s가 음수면 음수만큼 내려온 index로 취급한다.)
- substring(s,e) : s부터 e까지 자른다.(slice와 다르게  s or e가 음수이거나 NaN이면 0을 사용한다.)
- substr(s,l) : s부터 l길이 만큼 문자열을 자른다.
- length() : 문자열의 길이를 반환한다.
- toString() : 객체를 문자열로 변경한다.
- push(value) : 배열 요소 뒤에 value를추가한다.
- unshift(value) : 배열 요소 맨 앞에 value를추가한다.
- join(value) : 배열에 특정 구분자를 넣어 문자형으로 변환한다.
- sort(comp) : comp비교를 통해 정렬가준을 정한뒤 정렬한다.
- some(condition) : 배열 요소가 특정 조건을 만족하면 true를 반환과 동시에 함수 종료
- every(condition) : 모든 배열 요소가 특정 조건을 만족하면 true를 반환 그렇지 않으면 false를 반한과 동시에 함수 종료
- find(condition) : 배열에서 조건에 만족하는 첫 번째 요소를 반환한다.
- filter(condition) : 배열의 특정 조건을 만족하는 요소들만 새로운 배열을 만들어 반환한다.
- map(e) : 배열의 요소를 일괄 변경해야 하는경우(ex e.id = "#id"+e.id)
- reduce((sum,e){return sumValue;},startValue) : 배열 내 값을 누적시킨다.
- Object.keys(obj) : 객체에서 키만 추출한다.
- Object.values(obj) : 객체에서 값만 추출한다.
- Object.entries(obj) : 객체를 배열로 변환한다.
- Object.freeze(obj) : 객체가 변경되지 않도록 설정한다.
- Object.assign(returnObject,...assignObject)
- JSON.stringify(value,replacer,spaceNumber) : JSON을 문자열로 변환한다.
- JSON.parse(json) : JSON문자열을 JSON으로 변경한다.
- setTimeout(function{},time) : time 시간 후에 function을 호출한다.
- setInterval(function{},time) : 일정time마다 function을 호출한다.

### Promise
- 비동기를 처리하기 위해 만들어졌다.
- 처리 후 완료되면 하나의 값을 결과로 반환한다.
    + Pending : 아직 결과가 없는 상태이다.
    + Fulfilled : 성공적으로 완료된 상태이다.
    + Rejected : 처리가 실패한 상태이다.
    

### Async
- 비동기 작업을 제어하기 위해 만들어졌다.
- `await`와 함께 써야하며 반드시 `async`함수 안에 있어야 한다.

