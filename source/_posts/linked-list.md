---
title: JS 資料結構 - Linked List
date: 2023-03-04 23:50:33
tags:
  - LINKED-LIST
  - DATA-STRUCTURE
categories: 
  - DATA-STRUCTURE
---

> JS 資料結構系列皆為 [資料結構與演算法 (JavaScript)](https://www.udemy.com/course/algorithm-data-structure/) 學習筆記。

## Linked List 介紹

`Linked List` 為一種與 `Array` 類似的資料結構且為 linear collection 會將所有的 element 通過線性的方式串起來，排列順序並不是依照存在記憶體裡面的位置順序做排序，而是通過每一個 element 會指向的下一個 element 做排序，因此在電腦的記憶體儲存位置上是不連續的。

Linked List 只會包含 head & length 兩個 property，而其由多個 node 組成，每個 node 則會包含 value 及 pointer，value 可以是 number 、 string 或是其他各種資料， 而 pointer 則代表了會指向另外一個 node 或是 null。

<!-- more -->
## 建立 Linked List

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
    this.length = 0;
  }
}
```

### Push

將 next 指向新的 node

```js
  push(value) {
    let newNode = new Node(value);

    if (this.head === null) {
      this.head = newNode;
    } else {
      let currentNode = this.head;
      while (currentNode.next !== null) {
        currentNode = currentNode.next;
      }
      currentNode.next = newNode;
    }
    this.length += 1;
  }
```

### Pop

return 第 n 個 node 並將 n-1 個 node 改為指向 null

```js
pop() {
    if (!this.head) {
      return null;
    }

    if (this.length == 1) {
      const temp = this.head;
      this.head = null;
      this.length = 0;
      return temp.value;
    }

    let currentNode = this.head;
    for (let i = 0; i < this.length - 2; i += 1) {
      currentNode = currentNode.next;
    }
    const temp = currentNode.next;
    currentNode.next = null;
    this.length -= 1;
    return temp.value;
  }
```

### Shift

將 head 的 node 改為第 1 個 node ，並將原先的 head return 

```js
shift() {
    if (!this.head) {
      return null;
    }

    if (this.length == 1) {
      const temp = this.head;
      this.head = null;
      this.length = 0;
      return temp.value;
    }

    const temp = this.head;
    this.head = this.head.next;
    this.length -= 1;

    return temp.value;
  }
```

### Unshift

head 改為新的 node 並將 next 指向原先的 head node

```js
unshift(value) {
    const newNode = new Node(value);

    if (!this.head) {
      this.head = newNode;
    } else {
      const temp = this.head;
      this.head = newNode;
      this.head.next = temp;
    }

    this.length += 1;
  }
```

### InsertAt

將 index - 1 的 next 指向新 node ，再將新 node 指向原先在 index 個的 node

```js
insertAt(index, value) {
    if (index > this.length || index < 0) {
      return null;
    }

    if (index === 0) {
      this.unshift(value);
      return;
    }

    if (index === this.length) {
      this.push(value);
      return;
    }

    const newNode = new Node(value);
    let currentNode = this.head;
    for (let i = 0; i < index - 1; i += 1) {
      currentNode = currentNode.next;
    }

    newNode.next = currentNode.next;
    currentNode.next = newNode;
    this.length += 1;
  }
```

### RemoveAt

將 index - 1 的 node 指向 index + 1

```js
removeAt(index) {
    if (index < 0 || index > this.length) {
      return;
    }

    if (index === 0) {
      this.shift();
      return;
    }

    if (index === this.length) {
      this.pop();
      return;
    }
    let currentNode = this.head;
    for (let i = 0; i < index - 1; i++) {
      currentNode = currentNode.next;
    }

    currentNode.next = currentNode.next.next;

    this.length -= 1;
  }
```

## Linked List 優點

### 無限增加元素

Linked List 不需要像 Array 一樣事先取得固定的記憶體，再新增元素時只需要改變 next 指向新的 node。

### 快速刪除及移除元素

在 Array 當中若是有 n 個元素，當要插入第 k ( k < n )個元素時，k + 1 ～ n 的記憶體位置都需要往後移動，反之如果是刪除第 k 個元素的話就需要將後面的元素都往前移動

不過在 Linked List 上時只需要改變前後 node 的 next 就可以了。

## Linked List 缺點

### 需要較多的記憶體

在 Linked List 裡，我們所使用的 node 包含著 value 跟 next ，與 Array 相比的話需要多記憶 next 的資料，因此會需要比較多的記憶體空間。

### 需要從 head 開始

在這邊文章中使用的都是 singly Linked List ，因此都需要從 head 開始找到所需的節點。

## 時間複雜度

|                                      | Single Linked List |
| ------------------------------------ | ------------------ |
| Accessing Elements                   | O(n)               |
| Insert and Remove from the Beginning | O(1)               |
| Insert and Remove from the End       | O(n)               |
| Insert and Remove from the MIddle    | O(n)               |

<sub><sup>[資料結構與演算法 (JavaScript)](https://www.udemy.com/course/algorithm-data-structure/)</sup></sub>
