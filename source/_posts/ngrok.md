---
title: 讓別人看看 - ngrok
date: 2023-02-28 00:20:02
tags:
  - ngrok
  - develop
  - server
categories: 
  - DEVTOOL
---

筆記一下一款好用的開發工具 [ngrok](https://ngrok.com/)，這款工具可以讓其他人看到自己開發機的內容。

<!-- more -->
## 註冊及設定 ngrok

首先我們到官網註冊 ngrok，並且下載安裝在自己的電腦。

這邊我是使用 homebrew 安裝的

```bash
brew  install ngrok --cask
```

註冊成功後就會到他的 dashboard ，左邊側邊欄找到 `Your Authtoken` 點進去之後就可以看到自己的 token。

![ngrok token](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/02/28/5sts8t.png)

照他提供的 command line 設定 token 就只需要設定一次就好，看起來也可以依照各專案去設定但是我本人沒這個需求所以就設定一次就好。

```bash
ngrok config add-authtoken your-token
```

接著就來試試看到底效果怎麼樣吧。

## 測試 ngrok

我們直接借用 vscode 的 extension `Live Server` 起一個 local server。

![live server](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/02/28/WpEVq2.png)

接著建立一個 html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ngrok test</title>
</head>
<body>

  <h1>ngrok test</h1>
  <p>ngrok is working</p>

  <script>
    alert('ngrok is working');
  </script>
  
</body>
</html>
```

預設的 live server 會定在 5500 port，開啟後我們就把 ngrok 打開來並且指定 port 號。

```bash
ngrok http 5500
```

![setup ngrok server](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/02/28/PoDfQ2.png)

接著開啟手機使用任意網路，輸入 ngrok 提供的連結，以我的例子來講的話是 `https://d18d-1-160-160-128.jp.ngrok.io`

![ngrok 引入 js 正常](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/02/28/y7VXpp.jpg)

![html 載入正常](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/02/28/bRwAHg.jpg)

## 我的待解之謎

由於我個人開發是會用到 wordpress 的，並且我有更改我本機的 host 以及加入 ssl ， 因此我希望 ngrok 也可以在這邊達到一樣的效果，首先 port 設定成 443 就可以自然而然的變成 https。

```bash
ngrok http 443
```

![ngrok local ssl](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/02/28/eCCRkU.png)

再來我們可以通過 `--host-rewrite` 來設定 host。

```bash
ngrok http --host-header=rewrite test.com:443
```

![ngrok rewrite host](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/02/28/sPTeHx.png)

這邊以我的情況來說我必須這樣使用才能打開 local 的 wordpress。

```bash
ngrok http --scheme=https --host-header=rewrite test.com:80
```

![wordpress 範例](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/02/28/1CDr9H.png)

不過這種狀況下我只能進到首頁，並且看起來是只能拿到 html，再點選內部連結或者是 css 似乎因為都還是 `test.com` 所以在 ngrok 在取得的時候會有問題，也有可能把我本地的 nginx 處理一下就可以，總而言之需要再研究一下，將來研究出來再補上。

<style>
  img[alt='ngrok 引入 js 正常'],
  img[alt='html 載入正常']{
    max-width:400px;
  }
</style>
