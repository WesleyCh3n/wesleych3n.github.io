---
title: "Name Export vs Default Export"
date: 2021-10-15
categories:
  - note
tags:
  - javascript
toc: true
toc_label: "Outline"
toc_sticky: true
toc_icon: "box-open"
header:
  teaser: ./assets/teasers/code-bg.png

---

## Name Export

- Export

```javascript
export const Hello = () => {
  return <h1>Hello</h1>;
}

export const Goodbye = () => {
  return <h1>Goodbye</h1>;
}
```

We can export multiple components from a single file.

- Import

```javascript
import { Hello, Goodbye } from "./Greetings"
// or
import * as Greetings from "./Greetings"
<Greetings.Hello />
```

## Default Export

- Export

```javascript
const Hello = () => {
  return <h1>Hello</h1>;
}

export default Hello;
```

only export one component per file;

If you want multiple functions in a file

```javascript
const fn1 = () => {}
const fn2 = () => {}

export default { fn1, fn2 }
```

- Import

Single functions

```javascript
import Hello from "./Hello"
```

Multiple functions

```javascript
import Fns from "./functions"

Fns.fn1();
Fns.fn2();
```

## TL;DR

`Default` is better to prevent same function name in different file.

```javascript
import EN from './EnGreetings';
import TW from './TwGreetings';

const render = () => {
  return (
    <div>
      <EN.Hello />
      <TW.Hello />
    </div>
  )
}
```
