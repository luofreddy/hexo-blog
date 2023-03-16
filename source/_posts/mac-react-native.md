---
title: Mac 建立 React Native
date: 2023-03-09 00:03:49
tags:
	- MACOS
	- REACT
	- REACT
	- REACT-NATIVE
	- TYPESCRIPT
categories:
	- MOBILE-APPLICATION
---
筆記一下在 Mac 中建立起 React Native 時的過程。

<!-- more -->

## 安裝 Expo-Cli

```bash
npm i -g npm install -g expo-cli
```

## 建立專案

```bash
expo init first-app
```

建立好後輸入

```bash
npm run ios
```

這時他可能會叫你安裝 `XCode`，就會導到 App Store 要你安裝，安裝完之後要記得點開來把 ios 的環境基本裝一下。

好了之後就再次回到 command line 輸入 
```bash
npm run ios
```

如果他一直不斷叫你去安裝的話，那就跟著接下來的步驟做。

1. 首先先打開 XCode 的 setting，從左上角的 Xcode 裡面可以找到。
2. 找到 `Locations` 下面有個 Command line tool 選一下旁邊的 dropdown，你可能原本就會有一個值了，但這邊還是點選一下。
	![Xcode Command line tool](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/03/09/GnRr4M.png)

3. 接著應該就可以正常啟動了
	![啟動 ios 模擬器](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/03/09/m0klQq.png)