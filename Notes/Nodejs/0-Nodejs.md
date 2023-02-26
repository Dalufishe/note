# Node.js

## 學前須知

- Node 是 JS 的運行環境 (runtime)。
- Node 使前端開發者可更容易進入後端開發，因為他就是 JS。
- Node 是大量底層平台/工具 (如 webpack) 的開發語言。
- Node 擁有廣大的社群支持。

## Node 技術棧

- Node.js 基礎
- Express & Koa2
- MongoDB & MySQL
- Mocha

## 瀏覽器 vs Node

- Node 將瀏覽器的 V8 引擎搬下來，實現運行 JS。
- Node 提供了許多了許多瀏覽器上沒有(或禁止) 的功能 (安全問題等考量)
  - 檔案讀寫
  - 進程管理
  - 網路通信...

## Node - 模塊化開發

- 傳統瀏覽器可選擇使用非模塊化或模塊化開發方式。
- Node 只能使用模塊化開發方式，並符合 CommonJS 規範。
- 為什麼使用模塊化開發 ?
  - 模塊化開發相較非模塊化開發，命名空間獨立，代碼組織整齊，且不會有無法預期的依賴關係問題。

## CommonJS 的模塊化規範

- CommonJS 為一 JS 規範，為 Node 所用。
- CommonJS 中的模塊化 (modules) 規範規定了 require 和 export 做模塊化開發。
- require( FILEPATH"): 導入模組
- module.exports = {module}: 導出模組

## npm & yarn

- npm 最初作為 Node.js 的第三方模組管理系統，可以很方便地做第三方庫的下載，版本控制等功能。
- yarn 相較 npm 擁有更高速度及安全性等優勢。

## ES6 的模塊化規範

- Node 後期版本引入了 ES6 模組化規範，須設定附檔名 (.mjs) 或使用 npm 配置 package.json "type" = "module" 使用 ES6 模塊化寫法。

## 內建模組

- [http模組]("./1-http模組.md"): 網路處理