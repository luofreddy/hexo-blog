---
title: vite react unit testing 環境配置
date: 2023-03-03 00:00:26
tags:
	- VITE
	- REACT
	- JEST
	- TESTING
	- REACT-TESTING-LIBRARY
	- TYPESCRIPT
categories:
	- TESTING
---

## 前言

目前在公司使用 vite + react 的配置，最近需要導入 testing 在環境建置上遇到了一點問題為此記錄一下解決辦法。

<!-- more -->

## 建立 Vite React

![create react typescript project by vite](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/03/02/ROtx8z.png)


## 建立測試 Function 及 Unit Test
```ts
// add.ts

export function add(a: number, b: number): number {

return a + b;

}
```

```ts
// add.test.ts

import { add } from './add';


test('adds 1 + 2 to equal 3', () => {

expect(add(1, 2)).toBe(3);

}
```


## 配置 Jest

```bash
npm i -D jest @types/jest jest-environment-jsdom ts-node
```

建立 jest.config.ts 在根目錄
```ts
// jest.config.ts

export default {

	clearMocks: false,
	
	collectCoverage: true,
	
	coverageDirectory: "coverage",
	
	preset: 'ts-jest',
	
	testEnvironment: "jsdom",

};
```



## Babel 配置

我們需要配置 babel 讓我們可以用 es module 來寫 testing。

首先先來安裝套件
```bash
npm i -D babel-jest @babel/core @babel/preset-env
```

接著在根目錄建立 `babel.config.js`

```js
module.exports = {
    presets: [
        [
            '@babel/preset-env',
            {
                targets: {
                    node: 'current',
                },
            },
        ],
    ],
};
```

## 執行測試

```bash
jest
```

![jest testing result](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/03/02/GA5cRq.png)

## 配置 React testing Library

```bash
npm i -D @testing-library/jest-dom @testing-library/react @testing-library/user-event
```

接著建立 component 測試

```tsx
// button.tsx  
const MyButton = (props: { text: string }) => {
	return <button>{props.text}</button>;
};

export default MyButton;
```

```tsx
// button.test.tsx 注意這邊要是 tsx
import { render, screen } from '@testing-library/react';

import MyButton from './button';

  

test('renders my button', () => {

	render(<MyButton text='123'/>);
	
	const linkElement = screen.getByText('123');

});
```

接下來測試一下

![react testing library test](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/03/02/IEjrET.png)

## Reference
[Jest：建置測試環境 (包含 Babel)](https://titangene.github.io/article/jest-build-test-env.html)