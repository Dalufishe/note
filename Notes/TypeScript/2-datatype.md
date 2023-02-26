# TypeScript 資料類型

---

TypeScript 資料類型和 JavaScript 資料類型大致相同，多了枚舉等類型供使用。

### 布林值 (Boolean)

true / false 值的資料型別，在 JS 和 TS 裡叫做 `boolean`。

```ts
let isClick: boolean = false;
```

### 數字 (Number)

JS 和 TS 所有數字皆為浮點數。類型為 `number`。支持十進制 / 十六進制 / 二進制 / 八進制字面值。

```ts
let dec: number = 6; //十進制
let hex: number = 0xf00d; //十六進制
let bin: number = 0b1010; //二進制
let oct: number = 0o744; //八進制
```

### 字串 (String)

`string` 字串類型，可以使用 雙引號 (") 或單引號 (')，字浮串模板 (`) 字面值。

```ts
let user: string = "Eason";
let password: string = "24315451";
let crypted: string = `${crypt(password)}`;
```

## 陣列 / 數組 (Array)

TS 和 JS 一樣可以操作陣列元素。有兩種方式可以宣告陣列"靜態型別"。

- 在元素類型後面接上 [] :

```ts
let array: number[] = [1, 2, 3];
```

- 使用陣列泛型 :

```ts
let array: Array<number> = [1, 2, 3];
```

### 元組 (Tuple)

元組類型表示一個`已知`元素`數量`和`類型`的數組。各元素類型不必相同。

```ts
let tuple: [string, number];

tuple = ["hi", 123];
// OK
tuple = [123, "hi"];
// Error
```

當訪問一個越界的元素會報錯。

```ts
x[3] = "world";
// Error, Property '3' does not exist on type '[string, number]'.

console.log(x[5].toString());
// Error, Property '5' does not exist on type '[string, number]'.
```

### 枚舉 (Enum)

`enum`類型為一組數值給與友好的名字。(在 JS 中，就是限縮功能的物件，任務就是讓數值和名字相對應)。

```ts
enum Color {
  Red,
  Green,
  Blue,
}
console.log(Color.Red);
```

默認情況下，從 0 開始編號。你可以手動指定`起始數值`。

```ts
enum Color {
  Red = 1,
  Green,
  Blue,
}
```

或者，全部採用手動賦值 :

```ts
enum Color {
  Red = 1,
  Green = 3,
  Blue = 9,
}
```

除了透過名字得到數值，也可透過值得到名字 :

```ts
enum Color {
  Red,
  Green,
  Blue,
}
console.log(Color.Red); // name to value
console.log(Color[0]); // vaule to name
```

### 未知 (Unknown)

我們可能需描述一個`還不清楚其類型`的變數。在某種情況下，想讓編譯器、開發工具或開發者知道此變數可暫時是任意類型，並在之後能更加確定其類型，就會使用 `unknown` 類型。

```ts
let notSure: unknown;
notSure = "maybe a string instead";
// or boolean
notSure = false;
```

你可以對 `unknown` 類型的變量進行`類型檢查`或`類型斷言`，使其類型`更加精確`。

### 任意 (Any)

我們可能需描述一個`還不清楚其類型`的變數。在某種情況下，想讓編譯器或開發工具直接略過型別檢查，就會使用 `any` 類型來標記那些變數。

```ts
let notSure: any;
notSure = "maybe a string instead";
// or boolean
notSure = false;
```

- `any` 類型在對現有代碼改寫時十分有用。(可讓編譯器或開發工具略過型別檢查)。
- 使用 any[] 可表示 可以是任意元素的陣列。

你也可以對 `any` 類型的變量進行`類型檢查`或`類型斷言`，使其類型`更加精確`，但通常會使用 unknown 類別 而非 any 類型。

### 無 (Void)

某種程度上，void 類型為 any 類型的相反。他表示沒有任何類型。

- 當一個函式沒有回傳值，回傳值類型可設為 `void` :

```ts
function sayHello(): void {
  console.log("Hello");
}
```

- 預設情況下，void 類型其實就是 null 和 undefined 類型的集合 :

```ts
let u: void = undefined;
let v: void = null;
```

- 在開啟 `--strictNullChecks` 時，void 類型就僅僅能賦值為 undefined。

| 和 void 的關係       | null        | undefined   |
| -------------------- | ----------- | ----------- |
| `default`            | void 子類型 | void 子類型 |
| `--strictNullChecks` | 無          | void 子類型 |

### Null 和 Undefined

- TS 和 JS 一樣，null 表示空，undefined 表示未定義。並各自為各自類型的唯一值。
- 在 TS 中，默認情况下，null 和 undefined 是所有類型的子類型。也就是說你可以把 null 和 undefined 赋值给 number 類型的變數。
- 在開啟 `--strictNullChecks` 時，null 和 undefined 只能赋值给 any 和它们各自的类型（有一个例外是 undefined 还可以赋值给 void 类型）。

| 和所有類型的關係     | null               | undefined                  |
| -------------------- | ------------------ | -------------------------- |
| `default`            | 所有類型的子類型   | 所有類型的子類型           |
| `--strictNullChecks` | any 和自身的子類型 | any 、 void 和自身的子類型 |

### Never

`never` 类型表示的是那些永不存在的值的类型。

- never 類型常用於那些沒有回傳值的函式回傳值類型 :

```ts
// 擲出錯誤
function error(message: string): never {
  throw new Error(message);
}
// 值出錯誤
function fail() {
  return error("Something failed");
}
// 無限迴圈
function infiniteLoop(): never {
  while (true) {}
}
```

- never 类型是任何类型的子类型，然而，没有类型是 never 的子类型。

### Object

`object` 類型表示非原始類型，也就是除了 number, string, boolean, symbol, null, undefined 之外的類型。

### 類型斷言

有时候你會比 TypeScript 更了解某個值的詳細信息。

通過類型斷言這種方式可以告訴編譯器，“相信我，我知道我在幹甚麼”。類型斷言好比其它語言里的类型轉換，但是不进行特殊的数据检查和解构。(直接並且強制性的) 它没有运行时的影响，只是在编译阶段起作用。TypeScript 会假设你，程序员，已经进行了必须的检查。

類型断言有两种形式。 其一是“尖括号”语法：

```ts
let someValue: any = "this is a string";
```

let strLength: number = (<string>someValue).length;
另一个为 as 语法：

```ts
let someValue: any = "this is a string";
```

```ts
let strLength: number = (someValue as string).length;
```

两种形式是等价的。 至于使用哪个大多数情况下是凭个人喜好；然而，当你在 TypeScript 里使用 JSX 时，只有 as 语法断言是被允许的。
