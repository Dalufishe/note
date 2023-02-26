# url 模組

- url 模組提供了一些實用函數，用於 URL 的處理和解析。

### 導入

```js
const url = require("url");
```

### URL 字符串 & URL 對象

- 一个 "URL 字符串"是一个結構化的字符串，它包含多个有意義的组成部分。 当被解析時，會返回一个 "URL 對象"，它包含每个组成部分作為屬性。

##### url 模組提供了兩套 api 來處理 URL 對象:

- 舊式: node.js api (url.parse() // => 返回舊版 url 對象 )

```js
var myUrlObj = url.parse();
```

- 新式: WHATWG url standard api (new URL() // => 返回新版 URL 對象)

```js
var myUrlObj = new URL();
```

- [注] WHATWG url standard URL 对象的所有属性都是在类的原型上实现为 getter 和 setter。

##### WHATWG url standard api (舊式 node.js 遺留的 api 已被淘汰，不探討)。

- new URL(input[, base])

  - input: string , 要解析的输入 URL。
  - base: string | URL , 如果 "input" 是相对 URL，则为要解析的基本 URL。
  - [注] Unicode 字符将被使用 Punycode 算法自动转换为 ASCII。

````js
    var myUrlObj = new URL('/foo', 'https://example.org/');
    ```
````

- url.hash
- url.host
- url.hostname
- url.href
- url.origin
- url.username
- url.password
- url.pathname
- url.port
- url.protocol
- url.search
- url.searchParams
- url.toString()
- url.toJSON()
