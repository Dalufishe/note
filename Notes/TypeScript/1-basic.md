# TypeScript 基本概念

---

### 下載

- ##### 透過 npm

```bash
npm install -g typescript
```

### Hello World

- ##### 寫代碼

複製下列程式並加上`.ts`擴展名。
`註:` 下列程序僅僅為 JS 代碼，後續會為其加上 TS 新功能。

```ts
function sayhello(word) {
  return "Hello, " + word;
}

let word = "World";

document.body.innerHTML = sayhello(word);
```

- ##### 編譯代碼
  在命令終端輸入

```bash
tsc sayhello.ts
```

輸出結果為一個`sayhello.js`文件，運行他，你成功了！

### 類型註解

TypeScript 裡的類型註解是一種輕量的為函数或變數添加约束的方式。

- 為 word 參數加上 string 型別註解 :

```ts
function sayhello(word: string) {
  return "Hello, " + word;
}
```

- 若引數傳入陣列 :

```ts
let word = [1, 2, 3];

document.body.innerHTML = sayhello(word);
```

- TypeScript 編譯器會在終端機報錯 :

```bash
sayhello.ts:7:36 - error TS2345: Argument of type 'number[]' is not assignable to parameter of type 'string'.
```

- 若不加入引數 :

```ts
document.body.innerHTML = sayhello();
```

- TypeScript 編譯器會在終端機告訴你參數個數不符預期 :

```bash
sayhello.ts:5:27 - error TS2554: Expected 1 arguments, but got 0.
```

`注:` 在預設情況下，即使編譯器報錯，TS 仍會被編譯成 JS。

### 接口

在 TypeScript 中，我們使用接口為結構連接和命名。

```ts
interface Person {
  firstName: string;
  lastName: string;
}

function sayhello(person: Person) {
  return "Hello, " + person.firstName + "" + person.lastName;
}

let person = {
  firstName: "Dalu",
  lastName: "Fishe",
};

document.body.innerHTML = sayhello(person);
```

### 類

TypeScript 支持 JavaScript 的新特性，如物件導向程式設計。

```ts
class Student {
  fullName: string;
  constructor(
    public firstName: string,
    public middleInitial: string,
    public lastName: string
  ) {
    this.fullName = firstName + " " + middleInitial + " " + lastName;
  }
}
```

---
