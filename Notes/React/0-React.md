# React

<img
src="https://ms314006.github.io/static/b7a8f321b0bbc07ca9b9d22a7a505ed5/97b31/React.jpg"
height="180px"
style="margin-left: 20px">

---

## 學前須知

+ React 是 *用來實作使用者介面 ( UI ) 的 JavaScript 函式庫* - by [React官網](https://reactjs.org/)
+ React 實際上僅為 JS 函式庫，需搭配其他第三方函式庫 (如狀態管理) 完善框架體系。
+ 學習 React 需有熟練 JavaScript 及 ES6 語言標準，及 HTML 和 CSS 基礎。
+ 快速認識 React [點擊這裡 ( React in 100 Seconds )](https://www.youtube.com/watch?v=Tn6-PIqc4UM&t=30s&ab_channel=Fireship)。

---

## 簡介

+ React並非傳統的 MVC 架構，只能算是 UI 函式庫 (可加以改造成 Flux 架構)。
+ 由 FaceBook, Jordan Walke 創造，並與開源社群協同開發維護。
+ 為開放原始碼的 Javascript 函式庫。
+ 世界上最廣泛使用的前湍網頁框架。

---

## 特色

+ 聲明式 (宣告式) 編程 :
  + 主要使用聲明式編程。不同於傳統命令式編程。
  + 透過操作狀態 (渲染數據)，並搭配 React-自動更新完成頁面更新，而非所有細節都由開發者自己操作。
  + 可提高開發效率。
+ 整潔, 效率高 :
  + 原生JS操作DOM ( DOM API ) 繁瑣，效率低。
  + JQuery操作DOM ( JQuery API ) 提供簡潔語法，但仍效率低 (操作不當瀏覽器會進行大量重繪重排 )。
  + React使用"虛擬DOM" + Diffing算法，減少與真實DOM交互，大幅提高效率。
+ 高靈活性 :
  + React能和已知庫和框架很好的配合。
+ React組件化 :
  + 使用組件化，使組件能重複使用。
  + 組件使頁面保持整潔。
+ JSX語法 :
  + Javascript語法的擴展，為 Javascript + XML，將 XML 整合進 JS中，方便進行開發。
+ 單向響應式的數據流 :
  + 不同於傳統數據綁定，更容易使用
+ 使用 React語法進行移動端 :
  + 學會React，可使用 React Nactive 開發移動端。

---

## 安裝

+ 安裝 [NodeJS](https://nodejs.org/en/)。
+ 建立 React App 透過 :

```bash
$ npx create-react-app my-app

// 官方提供的開發包，省去了手動建置環境的時間。
```

+ 開始你的 React之旅

---

## Hello World

+ 引入 React 模組，使編譯後的 JS 檔案支援 JSX 語法 (注: 新版本已經被自動導入，可選擇性加入)。

```js
import React from "react";
```

+ 引入 ReactDOM 模組，用於渲染。

```js
import ReactDOM from "react-dom";
```

+ 透過 ReactDOM 的 render 方法，渲染 \<div>Hello World\</div> 到 id 為 root 的節點之下。

```js
ReactDOM.render(<div>Hello World</div>, document.getElementbyId("root"))
```

---

## 下一篇 : [JSX 語法](./1-JSX.md)
