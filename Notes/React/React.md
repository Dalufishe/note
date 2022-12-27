# React

<img
src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a7/React-icon.svg/1200px-React-icon.svg.png"
width="80px"
style="margin-left: 20px">

+ *用來實作使用者介面 ( UI ) 的 JavaScript 函式庫* - by [React官網](https://reactjs.org/)
+ React 實際上僅為 JS 函式庫，需搭配其他第三方函式庫 (如狀態管理) 完善框架體系

## 簡介

+ React並非傳統的 MVC 架構，只能算是 UI 函式庫 (可加以改造成 Flux 架構)。
+ 由 FaceBook, Jordan Walke 創造，並與開源社群協同開發維護。
+ 為開放原始碼的 Javascript 函式庫。
+ 世界上最廣泛使用的前湍網頁框架。

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
