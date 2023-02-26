# http 模組

- 導入

```js
const http = require("http");
```

- 建立伺服器

```js
http
  .createServer((req, res) => {
    //* 接收瀏覽器請求, 發出回應。

    //* 撰寫內容
    res.write();
    //* 結束回應(必要)
    res.end();
  })
  .listen(3000, () => {
    console.log("server start");
  });

// 或


const server = http.createServer();
server.on("request" (req, res) => {
    //* 接收瀏覽器請求, 發出回應。

    //* 撰寫內容
    res.write();
    //* 結束回應(必要)
    res.end();
  })
server.listen(3000, ()=>{
  console.log("server start");
})
```

- 請求 & 回應

  - req : 瀏覽器請求
  - res : 伺服器回應
  - res.writeHead(status, header): 撰寫狀態及響應頭
  - res.write(): 撰寫頁面
  - res.end(): 結束回應

- 伺服端路由

  - 透過操作 req.url 實現伺服端路由。
