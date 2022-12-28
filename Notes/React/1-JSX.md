# JSX

<img
src="https://blog.waterstrong.me/assets/jsx-syntax/jsx_logo.png"
height="120px"
style="margin-left: 20px">

## 概念

+ JSX = JS + XML，為 JavaScript 的擴充。
+ JSX 可使開發者在 JS 中 撰寫 XML 語法，簡化開發難度和提高開發效率。
+ JSX 會通過 Babel 編譯器將 JSX 程序 轉為純 JS 程序。
  + [注] : Babel，一種編譯器、轉譯器，能夠使軟體開發者以偏好的程式語言或風格來寫作原始碼，再透過 Babel 編譯器將其轉為 JavaScript。

```jsx
import React from "react";

// 導入 React 後面要用

<a href="https://github.com/Dalufishe">This is a Link</a>

// 這是一段 JSX 代碼，能夠被撰寫在 JS 中 XML 代碼

React.createElement("a", {href: "https://github.com/Dalufishe"} );

// 被 Babel 編譯器轉換成的 純 JS 代碼 
```

## 標籤

+ 和 XML 的語法絕大部分重疊。如 :

```js
<p>hello</p>

// 文章區塊元素

<a>a link</a>

// 超連結元素

<input />

// 輸入框元素
```

+ JSX 標籤支持 XML 標籤和 [React 組件](./2-Component.md)標籤。

## 使用 JS

+ 我們可以透過 曲括號 (大引號) 在 JSX 語法中使用 JS 運算式。

```js
const x, y = 1, 2;
React.render(<div>{ x + y }<div>, ...)

// 在頁面顯示被區塊包住的文字 3 
```

+ 曲括號運算提供了寬容的轉換方式，許多資料型態都可被轉為能在頁面上顯示的資料。

## 屬性

+ 在標籤中可加入屬性 (類似 XML 屬性語法)。
+ 在 XML 標籤中大部分屬性為原本 XML 的屬性。
  + [注] : 某些屬性名稱可能有變動，如 class 屬性被改為 className，事件處理器統一 on 後面大寫 (如 onClick )，而極少部分可能功能有改變，如 input 框的 Change 事件 並非原本 綁定在 XML 屬性上的 JS 事件功能。
+ React 組件標籤可設置自己的屬性。
+ 少數屬性為 React 規定的附有特殊意義的屬性，如 key 屬性有助於提高 diffing 算法效率。

```js
<span 
    className="fruits"
    style={{
        color: "red",
        display: "absolute",   
    }}
    onClick={{console.log("yes? Apple!")}}
>apple</span>
```
