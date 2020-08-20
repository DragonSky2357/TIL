# CSS(Cascading Style Sheets)
- 웹페이지를 어떻게 렌더링을 할것인지 정의
- HTML이 몸이라면 CSS는 스타일리쉬(화장,옷)임
- 웹을 만드는데 꼭 필요하지는 않지만 CSS를 적용을 했을경우 색다른 웹이 만들어짐
- 현재까지 CSS3 발표됨

## 1. CSS의 기본 문법

### 1.1 Selector(선택자)
원하는 스타일을 적용하고자 하는 HTML태그를 이용하여 적용함

```
p {font-size:16px; color:blue}
.class {padding:10px; margin:20px;}
#id {border:1px; background:#ffffff;}
```

### CSS 키워드
[CSS 키워드]: https://developer.mozilla.org/ko/docs/Web/CSS/Reference


### 1.2 Attribute(속성)
Attribute는 Element의 시작 태그 안에서 사용되는 것으로 성질, 특징등의 구체화된 정보를 제공한다.
또한 Attribute의 Name과 Attribute의 값은 한 쌍을 이룬다.
```
<img src="example.png"> 
```

### 1.3 Comments(주석)
코드를 설명하기 위해 사용되고 화면에 표시는 하지 않는다.
```
<!-- 화면의 표시되지 않는다-->
<p>Hello World</p>
```
