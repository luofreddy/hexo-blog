---
title: 那年我的前端自學資源
date: 2023-02-26 23:33:08
tags:
  - FRONTED
  - REACT
  - HTML
  - JAVASCRIPT
  - CSS
categories: 
  - FRONTEND
---

## 前言

取之於社會，用之於社會，在轉職前看到了很多前輩、大神分享的自學資源，於是在正式轉職一年後的我也來分享一下我自己當初學習的資源，另外有覺得不錯的資源我也會不定時的更新。

<!-- more -->

## 前端工程師 roadmap

![f2e roadmap](https://github.com/goodjack/developer-roadmap-chinese/blob/master/chinese-version/img/frontend.png?raw=true)

## 通用資源

### [MDN](https://developer.mozilla.org/zh-TW/)

MDN 就不解釋了，在學習的一路上你都會一直用到它。

### [stackoverflow](https://stackoverflow.com/)

stackoverflow應該也不用解釋，你工作很需要它。

### [Front-End Developers Taiwan](https://www.facebook.com/groups/f2e.tw/)

前端的 FB 社團，裡面藏了不少大神，看到別人有問題時可以看看別人的回答會獲取意外的小知識。

### [Lidemy 鋰學院](https://lidemy.com/)

前端有名的 huli 建立的課程，可以照著他給的[學習地圖](https://lidemy.com/p/roadmap)上，當時我是使用訂閱 1 個月的方案，就把所有課上的差不多了，個人認為 CP 值蠻高的。

### [starbugs](https://weekly.starbugs.dev/)

由一群喜歡寫文章的工程師所組成，每週二會估定推出電子報分享國內外各個他們經過篩選覺得不錯的文章，但範圍不限定前端，也會有後端、web3、DevOps。

## HTML

個人覺得 html 是不用太花時間自學的，不過還是瞭解一下 html 5 比較好，尤其 SEO 也會是前端工程需要考慮的一部分，因此選擇語意化的標籤也是很重要的。

推薦資源：

### [HTML (HyperText Markup Language) 教學](https://www.fooish.com/html/)

基本上就是大致看過就可以，HTML5 的標籤可以多花點時間了解一下跟其他標籤不同的地方在哪裡，另外標籤的屬性也可以多了解一下，不過很多實務上需要再查就好，特別可以看一下 input type 這個屬性對於 mobile 來說會比較有影響的是在手機上彈出的鍵盤會根據 type 會有變化。

## CSS

CSS 方面也是有分版本，現在主流就是 CSS3 ，大部分的功能各家瀏覽器支援的程度都差不多，實在不確定的話可以上 [Can I Use](https://caniuse.com/) 查詢一下語法的支援性，另外在切 EDM 的時候由於大部分的信箱軟體都只支援到 CSS2 ，在使用之前可以先到[Can I Email](https://www.caniemail.com/) 查詢，另外如果 EDM 需要做 RWD 可以直接考慮使用 [MJML](https://mjml.io/)，最後小小提醒，很多時候 CSS 也是要考慮到瀏覽器效能，因此在撰寫得時候能達成目標的寫法可能有好幾種，不過至於哪一種比較好就需要透過大量的查看文章來學習。

推薦資源：

### [金魚切版系列教學](https://www.youtube.com/playlist?list=PLqivELodHt3hxeuLX8PYaI8u1GcDaBoJo)

Coke 老師在 CSS 教學上在台灣是蠻有名且蠻易懂的，大部分的自學資源也都會推他，這份系列影片就是切版練習，影片當中也會講解不少 CSS 原理，熟悉原理有助於前端 debug。

### [CSS !important: Don’t Use It. Do This Instead](https://uxengineer.com/css-specificity-avoid-important-css/)

首先 `!important` 在一個需要長時間維護的專案絕對不是一個好解法，善用 CSS 權重可以更優雅地覆蓋 CSS

小技巧：

```html
<div class='hello'>
</div>

<style>
.hello.hello{      // 可以將相同的 class 串接起來來增加該樣式的權重
  color: #ff0000;
}
</style>
```

### [30個你必須記住的CSS選擇器](https://code.tutsplus.com/zh-hant/tutorials/the-30-css-selectors-you-must-memorize--net-16048)

這沒什麼好說的，必看！

### [Select the plates](https://flukeout.github.io/)

CSS selector 小遊戲，看完上面的文章後可以拿這個練練手。

### [FLEXBOX FROGGY](https://flexboxfroggy.com/)

CSS flex 小遊戲，flex 是一個很常用的屬性，可以透過這個來學習

### [GRID GARDEN](http://cssgridgarden.com/)

CSS grid 小遊戲，一樣是一個前端很常用的屬性

### [CSS垂直置中技巧，我只會23個，你會幾個](http://csscoke.com/2018/08/21/css-vertical-align/)

這應該是我目前看到收錄最多方法的一篇文章了，很值得一看，不過實不實用是另外一回事。

## JavaScript

### [The Modern JavaScript Tutorial](https://javascript.info/)

講得非常完整跟詳細，章節也切分得很好，每一小章節也有小小練習題，不過也實在是太細了我自己也沒有全部看完。

### [所以說event loop到底是什麼玩意兒？](https://www.youtube.com/watch?v=8aGhZQkoFbQ&t=980s)

非常簡顯易懂的講解了 event loop 跟 call back function

### [ECMAScript 6 入门](https://es6.ruanyifeng.com/)

現在最通用的 JS 版本 ES6 是一定要學的，但這份資源是我後來有了工作之後才找到的所以我實際上沒有看過，不過看蠻多人都推的所以也放一下，要注意的是裡面有些大陸用語跟我們常用的可能會不一樣。

## React

React 基本上太多教學了，這邊就只推薦兩個一個是透過間單實作 todo list 了解 react ，另一個就是官方文件，官方文件真的是蠻多細節可以看的，其餘的資源就是有需要的時候才去找所以我就不放了。

### [【前端速成】React 快速入門｜Tiktok工程師帶你入門前端｜布魯斯前端](https://www.youtube.com/watch?v=zqV7NIFGDrQ&t=2s)

### [React 官方文件](https://zh-hant.reactjs.org/) ( [React beta docs](https://beta.reactjs.org/))
