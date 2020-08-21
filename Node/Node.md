# Node.js
- Node.js는 서버(Server)와 관련된 기술이다.
- 서버-클라이언트 모두 JS로 개발한다.
- V8 엔진이 JS코드를 기계어로 변환한다.

## Node.js 서버 실행
- node (name).js로 실행시킨다.

```
const http = require("http");

const HOST = "127.0.0.1";
const PORT = 5000;

const app = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader("Content-Type", "text/plain");
  res.end("Hello World");
});

app.listen(PORT, HOST, () => {
  console.log(`Server running Host:${HOST} Port:${PORT}`); // Server running Host:127.0.0.1 Port:5000
});
```

## Node.js 모듈
- Node.js는 CommonJs의 모듈화를 지원한다.
- 모듈 선언은 module.exports를 사용한다.
- 모듈을 가져올때는 require()를 사용한다.
