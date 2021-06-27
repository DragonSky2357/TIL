
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

## Graph QL API
- 데이터를 효율적으로 연결할 수 있고, 요청의 수와 복잡성을 줄이고 클라이언트가 필요로 하는 데이터를 제공한다.
```
const port = process.env.PORT || 4000;
```

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
