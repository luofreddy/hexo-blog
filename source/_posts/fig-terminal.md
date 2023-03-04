---
title: Terminal 自動補全工具 - Fig
date: 2023-03-01 22:23:51
tags:
  - FIG
  - DEVELOP
  - TERMINAL
categories: 
  - DEVTOOL
---

## 為什麼不用 Wrap

前一陣子同事們就有分享 [fig](https://fig.io/) 這個好用的 terminal 工具，他的自動補全功能非常好用，包括安裝的套件的 command line 他都可以幫忙補齊，在前一陣子我也用過 [warp](https://www.warp.dev/)，不過有幾點讓我覺得我不太適合使用它。

<!-- more -->

### 不能顯示中文
  
  在工作時有時 commit message 還是需要輸入中文，這時使用 wrap 會再打注音的時候無法顯示，這讓我有點困擾。

### Autocomplete

wrap 的 autocomplete 在我按下 `tab` 時會直接選取預設的第一個檔案，比如說在日常工作中我都適用 command line 來輸入 git 指令，因此有時候我想要 `git add src/` 這樣來選取所有 src 底下的檔案時，由於他 autocomplete 的提示可能是出現 `git add src/index.js` 這種時候我如果輸入到一半，按下 `tab` 他會直接輸入完 `git add src/index.js`，而不是停在 src 的部分。

```bash
#我輸入 git add s

# wrap 的 autocomplete 提示
git add src/index.js

# 但我想要的是
git add src/
```

以上兩點是我覺得用起來最不適應的地方，不過將來如果有什麼新功能或改動的話，我還是很願意再用用看，畢竟 `rust` 寫的真的讓我覺得又帥又潮。

## 安裝 Fig

接下來就是我的安裝踩雷筆記，我在使用 `homebrew` 安裝後不知道為什麼一直會有問題，因此記錄一下。

首先我這邊是用 `homebrew` 做安裝，他會直接幫忙把 `fig` 加進環境變數，如果是下載檔案來安裝的環境變數就要另外設定，因為等等我們會用到 `fig` 指令。

```bash
brew install fig
```

完成之後你可以重啟你的 terminal 測試看看有沒有成功啟用，如果沒有的話那就要繼續跟我往下看，如果使用檔案安裝後想要改 homebrew 安裝，但在刪除的時候刪不掉的話可以考慮直接用指令刪除。

```bash
cd /System/Applications
rm -rf Fig.app
```

### 無法成功啟用

接著我先重新 restart。

```bash
fig restart
```

restart 完成後再呼叫 doctor，看看問題在哪裡

```bash
fig doctor
```

我再呼叫 `fig doctor` 時就有自動跳出開啟權限的地方，開啟之後我就可以正常使用了。

![fig active](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/03/01/QrH1m3.png)

最後小小感想，我覺得 fig  有 doctor 這個指令真的是蠻酷的，並且也很好的提供的解決方法跟解決訊息。
