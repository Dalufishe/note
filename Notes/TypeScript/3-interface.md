# TypeScript 接口

---

TypeScript 核心原則之一為對值提供所具有的`結構中的值`進行型別檢查。(又稱鴨子辨型法、結構性子類型化)。在 TS 中，接口的作用為透過一個名字為你的代碼定義契約。

任何有結構的型別都可以定義接口。

### 物件類型

根據 `{ name: string; sex: number; age: number }` `結構`定義 :

- `printPerson()` 所傳入的引數必須為一個必包含 `name` 、 `sex` 和 `age` 特性的一個物件。
- 函數內只能使用該參數物件的 `name` 、 `sex` 和 `age` 特性。

```ts
function printPerson(person: { name: string; sex: number; age: number }) {
  console.log(person.name + person.sex + person.age);
}

printPerson({name: string; sex: number; age: number})
```

- 使用接口 (interface)，作為結構定義和結構使用的橋樑，並為該結構命名:

```ts
interface Person {
  name: string;
  sex: number;
  age: number;
}
function printPerson(person: Person) {
  console.log(person.name + person.sex + person.age);
}
```

### 可選屬性

我們可以透過在屬性名字後面加入 `?` 表示結構中該屬性為可選。

```ts
interface SquareConfig {
  color?: string;
  width?: number;
}
```

### 唯讀屬性

我們可以透過在屬性名字前加入 readonly 關鍵字表示結構中該屬性為唯讀。

```ts
interface Point {
  readonly x: number;
  readonly y: number;
}
```

### 額外屬性檢查

TypeScript 對待字面值物件，會相比其他 (如一個變數) 更加嚴格。

```ts
interface Person {
  name: string;
  age: number;
}

function printPerson(person: Person) {
  //
}
```

- 傳入一個指向物件的變量 :

```ts
let person = { name: "Dalufishe", age: 16, sex: 0 };
print(person);
```

型別檢查允許目標類型(結構)不包含的屬性。

- 然而傳入物件字面值 :

```ts
print({ name: "Dalufishe", age: 16, sex: 0 }); // ERROR
```

會觸發額外的型別檢查 : 只允許目標類型(結構)目標類型包含的屬性，否則報錯。

- ##### 解決方法 :
  - 傳入變數
  - 類型斷言
  - `[propName: string]: any` "最佳解"

```ts
interface Person {
  name: string;
  age: number;
}

function printPerson(person: Person) {
  //
}
```

傳入字面值 (報錯)

```ts
// Error
printPerson({ name: "Dalufishe", age: 16, sex: 0 });
```

傳入變數

```ts
// OK
let person = { name: "Dalufishe", age: 16, sex: 0 };
printPerson(person);
```

類型斷言

```ts
// OK
printPerson({ name: "Dalufishe", age: 16, sex: 0 } as Person);
```

`[propName: string]: any` "最佳解"

```ts
// OK
interface Person {
  name: string;
  age: number;
  [propName: string]: any;
}
function printPerson(person: Person) {
  //
}
printPerson({ name: "Dalufishe", age: 16, sex: 0 });
```

### 函式類型接口

TS 中接口除了能描述普通物件結構外，也能描述各種擁有結構的物件，如函式或陣列。

- ##### 定義調用簽名 :

```ts
interface addBlogFunc {
  (title: string, content: string, createTime: number): boolean;
}
```

- 使用接口 :

```ts
const addBlog: addBlogFunc;
addBlog = function (
  title: string,
  content: string,
  createTime: number
): boolean {
  //
  return true;
};
```

`注:` 函式`結構`中的參數定義名稱和函式`實際`的參數名稱不必一樣，並且類型宣告不必重寫。

### 可索引類型接口

可索引的類型 (如陣列，映射) 也可以定義接口。

- ##### 定義索引簽名 :

```ts
interface StringArray {
  [index: number]: string;
}
```

Typescript 支持两种索引签名：字串和数字。

### 類類型"實體"及類"本身"接口

TypeScript 也能夠用接口來明確的強制一個 class 去符合某種結構。

```ts
interface BlogInterface {
  addBlog(title: string, content: string): boolean;
  deleteBlog(id: number): boolean;
  updateBlog(id: number, title: string, content: string): boolean;
  getBlog(id: number): { title: string; content: string };
}

class Blog implements BlogInterface {
  addBlog(title: string, content: string): boolean {
    return true;
  }
  deleteBlog(id: number): boolean {
    return true;
  }
  updateBlog(id: number, title: string, content: string): boolean {
    return true;
  }
  getBlog(id: number): { title: string; content: string } {
    return {
      title: "Adfafd",
      content: "Adfafdf",
    };
  }
}
```

接口描述了類的公共部分，而非公共私有兩部分。

`implements`關鍵字規範了類`實體`的結構。

直接操作類以規範了類`本身(靜態)`的結構。

```ts
interface ClockConstructor {
  new (hour: number, minute: number);
}

interface ClockInterface {
  tick();
}

const Clock: ClockConstructor = class Clock implements ClockInterface {
  constructor(h: number, m: number) {}
  tick() {
    console.log("beep beep");
  }
};
```

### 接口繼承

和類 (class) 一樣，接口也可以相互繼承。

```ts
interface Shape {
  color: string;
}

interface Square extends Shape {
  sideLength: number;
}

let square = {} as Square;
square.color = "blue";
square.sideLength = 10;
```

### 接口繼承類

當接口繼承了類類型時，他會將類的實體成員作為結構繼承給接口。這包含了 `private` 和 `protected` 成員，因此我們可利用此特性做繼承結構劃分。

```ts
class Control {
  private state: any;
}

interface SelectableControl extends Control {
  select(): void;
}

class Button extends Control implements SelectableControl {
  select() {}
}

class TextBox extends Control {
  select() {}
}

class ImageControl implements SelectableControl {
  // Error: Class 'ImageControl' incorrectly implements interface 'SelectableControl'.
  //  Types have separate declarations of a private property 'state'.
  private state: any;
  select() {}
}
```
