
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

## 포트 확장 옵션
- 로컬 개발 환경에서는 문제업이 작동하나 배포할 때는 다른 포트 번호로 지정할 수 있도록 해야한다.
```
const port = process.env.PORT || 4000;
```


## GraphQL API
- 데이터를 효율적으로 연결할 수 있고, 요청의 수와 복잡성을 줄이고 클라이언트가 필요로 하는 데이터를 제공한다.
- API를 위한 쿼리 언어이며 타입 시스템을 사용하여 쿼리를 실행하는 서버사이드 런타임이다.
- 특정한 데이터베이스나 특정한 스토리지 엔진과 관계되어 있지 않으며 기존 코드와 데이터에 의해 대체된다.

### 서버를 API로
- apollo-server-express 패키지를 사용하여 서버를 GraphQL 서버로 전환한다.
- apollo-server는 express,Connect,Hapi,Koa를 포함한 많은 Node.js 서버 프레임워크와 함께 동작하는 오픈소스 GraphQL 서버 라이브러리이다.
- 시각적인 도우미 및 GraphQL 플레이 그라운드를 제공한다.

```
const {ApolloServer.gql} = require('apollo-server-express');
```

- GraphQL은 형식 정의 스키마 리졸버(resolver)로 이루어져 있다.
- 리졸버(resolver)은 쿼리와 뮤테이션(mutation)을 처리한다.

// GraphQL 스키마 구성
```
const typeDefs = gql`
    type Query{
        name : type
    }
`;
```

// GraphQL 리졸버 구성
```
const resolvers = {
    type Query{
        name : () => function
    }
};
```

- GraphQL API를 제공하기 위해 관련설정 및 미들웨어를 추가하고 아폴로 서버 통합한다.

```
// 아폴로 서버 설정
server.applyMiddleware({ app, path: '/api' });

// 아폴로 GraphQL 미들웨어를 적용 및 /api로 경로 설정
const server = new ApolloServer({
  typeDefs,
  resolvers,
  
});
```

### GraphQL 기초
#### 스키마
- 데이터와 상호작용을 글로 표현한것이다.
- GrapQL은 스키마를 필요하며, API에 대한 엄격한 계획을 강제하기 위한것이며 스키마 내에서 정의된 데이터만 반환 및 상호작용을 수행한다.
- GrapQL 스키마의 기본 구성 요소는 객체 자료형이며 5가지(String,Bollean,Int,Float,ID) 스칼라 자료형이 내장되어 있다.
- 선택적으로 입력하는 필드 값, 필수적으로 포함되어야 하는 느낌표(!)를 사용한다.
```
type Pizza{
    id: ID!
    size: String!
    slices: Int!
    toppings: [String]
}
```

#### 리졸버(resolver)
- 해결사 라는 의미를 가지며 API 사용자가 요청한 데이터를 해결한다.
- 리졸버를 작성하려면 먼저 스키마에서 리졸버를 정의한 다음 JS코드 내에서 로직을 구현해야 한다.
- API에는 쿼리와 뮤테이션 두 가지의 리졸버가 포함된다.

##### 쿼리
- API에 특정 데이터를 원하는 형식으로 요청한다.
- 사용자가 요청한 데이터를 포함하는 객체를 반환한다.
- 쿼리는 데이터를 수정하지 않으며, 데이터에 접근만 허용된다.

##### 뮤테이션
- API에 특정 데이터를 수정할 때 사용한다.
- 쿼리와 마찬가지로 객체의 형태로 결과를 반환하며 일반적으로 수행한 작업의 최종 결과를 반환한다.

### API 적용하기
