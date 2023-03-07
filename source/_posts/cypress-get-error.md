---
title: cypress-get-error
date: 2023-03-07 11:27:26
tags:
  - WORDPRESS
	- END-TO-END
	- TESTING
	- CYPRESS
	- TYPESCRIPT
categories:
	- TESTING
---

## 前言

在使用 Cypress 的過程中可能因為要根據某些 DOM 存不存在而作出相應的操作，這時我們就可以使用這個方法。

<!-- more -->

## 範例

```typescript
cy.get("body").then(($body) => {
  // synchronously query for element
  if ($body.find("element").length) {
    // do something
   } else {
    // do something else
   }
})
```

## Reference

[Is it possible to handle errors during `.get`? We need to put a retry process in place.](https://github.com/cypress-io/cypress/issues/395#issuecomment-275499926)