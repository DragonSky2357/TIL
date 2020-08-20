# CSS(Cascading Style Sheets)
- 웹페이지를 어떻게 렌더링을 할것인지 정의
- HTML이 몸이라면 CSS는 스타일리쉬(화장,옷)임
- 웹을 만드는데 꼭 필요하지는 않지만 CSS를 적용을 했을경우 색다른 웹이 만들어짐
- 현재까지 CSS3 발표됨

## CSS의 기본 문법

### Selector(선택자)
원하는 스타일을 적용하고자 하는 HTML태그를 이용하여 적용한다.

```
Selector {...}
.class {...}
#id {...}
```

#### CSS 키워드
Link: [CSS 키워드](https://developer.mozilla.org/ko/docs/Web/CSS/Reference)


### Property(속성)
- HTML의 요소들을 선택하고 {}안의 속성들을 적용하여 다양한 스타일 만든다.
- 콜론(:)뒤에 여러가지 속성값들이 올 수 있다.
- 여러개의 속성들을 지정할 수 있으며 세미콜론(;)으로 구분한다.

```
div{
  background:...;
  padding:...;
}
```

### Value(속성값)
- 콜론(:)뒤에 속성값들을 지정하며 특정단위로 지정해야 한다.
- var()를 이용하여 속성값들을 리터널 타입이 아닌 변수처럼 지정할 수 있다.
- 마지막 뒤에는 세미콜론(;)을 삽입한다.

```
div{
  ...:#fff;
  ...:12px;
}
```

## CSS와 HTML 연동
- HTML안에 link태그 안에 css를 적용한다.

```
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="css/style.css">
  </head>
  <body>
    <p>Hello World</p>
  </body>
</html>
```
