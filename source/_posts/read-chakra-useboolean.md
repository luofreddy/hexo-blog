---
title: 閱讀 Source Code - useBoolean
date: 2023-03-16 22:45:11
tags:
  - CHAKRA-UI
  - REACT
  - REACT-HOOK
  - TYPESCRIPT
categories:
  - REACT
---

>此篇文章主要紀錄研究  [Chakra UI](https://github.com/chakra-ui/chakra-ui/) source code 的小小心得 & 筆記

<!-- more -->

## Use Boolean
這次要來看的是 `Chakra UI` 所提供的 hook `useBoolean` 。

```typescript
import { useMemo, useState } from "react"

type InitialState = boolean | (() => boolean)

export function useBoolean(initialState: InitialState = false) {
	const [value, setValue] = useState(initialState)
	
	const callbacks = useMemo(
		() => ({		
			on: () => setValue(true),	
			off: () => setValue(false),	
			toggle: () => setValue((prev) => !prev),
		}), []	
	)
	
	return [value, callbacks] as const
}
```


### As Const
這邊 `as const` 會將 `useBoolean` 的回傳定為 `readonly [value, callbaks]` ，因此第一個的回傳值必定是拿到這個 hook 的 state ， 第二個就會是這些 callback，並且是不能更改的。

### 輸入參數採用 Union
如果是我的話我可能會將輸入的 initialState 定義為 `boolean` 而已，但是他這邊也加上了一個會回傳 `boolean` 的立即函式，差別會如下

![使用 union 差別](https://raw.githubusercontent.com/luofreddy/images/main/uPic/2023/03/16/K8QK0A.png)

並且經過驗證發現  `useState` 在塞入 function 當參數時會把 return 值當入初始值 。

