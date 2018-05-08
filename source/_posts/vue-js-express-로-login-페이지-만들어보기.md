---
title: vue.js + express 로 login 페이지 만들어보기
date: 2018-05-07 03:23:47
tags:
---

먼저 express-generator와 vue-cli를 설치합시다.

`$ sudo npm install express-generator -g`
`$ sudo npm install -g vue-cli`

```
$ express --view=ejs backend
$ cd backend
$ npm install
$ DEBUG=backend:* npm start
```

`$ npm install` 을 하였을 때 사소한 에러(write after end 에러)가 발생하여 `$ npm install -g npm@5.6.0` 를 통해 npm의 버전을 낮춰주었습니다(기존엔 6.0.0).

이제 [http://localhost:3000](http://localhost:3000) 에 들어가면 실행을 확인할 수 있습니다.  

이제 vue를 적용해봅시다. 프롬프트가 나올 때는 그냥 쭉 엔터를 입력합니다.  

```
$ vue init webpack frontend
$ cd frontend
$ npm install
```

추가 설정이 없을 때는 [http://localhost:8080](http://localhost:8080) 에서 이를 확인할 수 있습니다.  

이제 Vue와 express를 연결해봅시다.

/frontend/config/index.js의 index 부분과 assetsRoot 를 express 쪽으로 변경해줘야 합니다.  

```
...
index: path.resolve(__dirname, '../../backend/public/index.html'),
...
assetsRoot: path.resolve(__dirname, '../../backend/public'),
...
```

그 다음 frontend 에서 `$ npm run build` 를 진행해주면, build가 완료됩니다. 그러면 /backend/public/index.html 파일이 생기고, 이제 이를 routes와 연결해야 합니다. /backend/routes/index.js를 다음과 같이 수정합니다.  

```
var express = require('express');
var path = require('path');
var router = express.Router();

router.get('/', function (req, res, next) {
  res.sendFile(path.join(__dirname, '../public', 'index.html'))
});

module.exports = router;
```

이제 다시 서버를 실행하면 [http://localhost:3000](http://localhost:3000) 에서도 vue를 확인할 수 있습니다.  
뒤에 나와 있는 #를 삭제하는 것은 밑의 Reference 를 참고합니다.  

## mongodb

mongodb, mongoose 부터 설치합시다.

```
$ sudo brew install monogodb
$ sudo npm install -g mongoose
```

db를 만들고 실행합시다.

```
$ mkdir db
$ mongod --dbpath ./db
```

```
$ npm install --save axios
```

## Reference
[[Node.js] express와 vue.js 환경설정](https://m.blog.naver.com/PostView.nhn?blogId=kangminser88&logNo=221146020394&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F)
