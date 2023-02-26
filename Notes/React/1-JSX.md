# JSX

<img
src="https://blog.waterstrong.me/assets/jsx-syntax/jsx_logo.png"
height="180px"
style="margin-left: 20px">

---

## 概念

+ JSX = JS + XML，為 JavaScript 的擴充。
+ JSX 可使開發者在 JS 中 撰寫 XML 語法進行開發，簡化開發難度和提高開發效率。
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

---

## 標籤

+ JSX 標籤是 <> 中放入一段文字，就像 XML 的標籤一樣。
  + 一段有意義的 XML 語句被稱作元素，通常是由起始標籤和結尾標籤加上內容所組成。
  + 當該元素沒有內容，結尾標籤可被省略，被稱作空白元素。

+ JSX 標籤支持 XML 標籤和 React 組件標籤。
  + XML 標籤 : 和 XML 大致重疊。
  + [組件標籤](./2-Component.md) : 標籤內放入 React 組件名稱，首字一定要大寫。

```js
<input />

// 輸入框元素

<MyButton />

// React 組件標籤
```

---

## 使用 JS

+ 我們可以透過 曲括號 (大引號) 在 JSX 語法中使用 JS 運算式。

```js
const x, y = 1, 2;
React.render(<div>{ x + y }<div>, ...)

// 在頁面顯示被區塊包住的文字 3 
```

+ 曲括號運算提供了寬容的轉換方式，許多資料型態都可被轉為能在頁面上顯示的資料。

---

## 註解

+ 在 JSX 語法使用註解的原理是在其中寫 JS 語句 並設置註解。

```jsx
<div>{/* 這是註解 */}</div>
```

---

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
    onClick={
    console.log("yes? Apple!")}
>apple</span>
```

---

## 事件處理器

+ 事件處理器可透過事件屬性進行綁定。
+ 在 React 中的事件是透過事件委託 (統一將事件掛載到跟元素上, #root )實作。
  + 然而 React 將事件細節 (如 evt 行參) 模擬成個別元素的事件去做回應，當作甚麼都沒發生一樣。

---

## 下一篇 : [React 組件](./2-Component.md)
