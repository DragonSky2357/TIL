# JavaScript
- 웹페이지를 동적으로 움직이게 만들어준다.
- HTML이 몸이라면 CSS는 스타일리쉬(화장,옷)이라면 JS는 스마트폰이다. 
- Node js 및 React js등 여러가지 분야로 확장됨

## JavaScript의 기본

### 기본적인 출력

```
var PI=3.14
console.log("Hello World"); // Hello World
console.log(${PI}); // 3.14
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
- `if` : 의사결정을 할 수 있는 조건문 true인 경우 실행(else if, else)도 동일하다.

```
if(표현식1){명령문1}
else if(표현식2){명령문2}
else {명령문3}
```

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
- `for` : for(초기값;조건식;증감식)으로 구성된다.

```
for(var i=0;i<5;i++){
    console.log(i) // 1 2 3 4 5
}
```

- `for in` : for(속성명 in 반복 대상)으로 구성되며 반복문을 통해 요소를 한개씩 가져와 속성명으로 선언과 동시에 할당한다.

```
var nations = ["Korea","China","Japan"]

for(var item in nations){
    console.log(item); // Korea China Japan
}
```

- `while` : 조건식이 ture일때 반복 실행 false일때 반복 중단 한 번도 실행하지 않을 수 있다.

```
while(true){
    console.log("infinite print"); // infinite print infinite print infinite print infinite print... 무한반복
}
```

- `do~while` : while과 다르게 무조건 처음은 조건에 관계없이 한번 실행하며 while();로 표시한다.

```
var count=0;

do{
    console.log(count); // 1 2 3
}while(count<3);
```
