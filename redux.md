# Redux

- [Redux](#redux)
  - [檔案架構](#檔案架構)
  - [使用方式](#使用方式)
    - [action](#action)
    - [Component](#component)

## 檔案架構

`moedules 底下每個 moedule 都各自有 css、action、route、reducer。`

```diff
    │
    ├─src
    │  ├─modules
!   │  │  └─ExampleModule
!   │  │      ├─css
!   │  │      │  └─index.css
!   │  │      ├─action.js
!   │  │      ├─index.js
!   │  │      ├─route.js
!   │  │      └─reducer.js
    │  .....
    │  └─components
    ├─app.js
    ├─reducers.js
    └─routes.js
```

## 使用方式

### action

1. action 存放共用的 function，有要使用API的都方在此檔案。
1. 如無共用的 function 可直接寫在頁面上。

- 在頁面上使用

```javaScript
// import function
import { yourFunction } from './action';

// 使用 Function
dispatch(yourFunction());
```

- 在 action 中的Ａ function 裡使用 Ｂ function

```javaScript
// 使用 Function
yourFunction()(dispatch);
// 如有帶store 也要附加上去
yourFunction()(dispatch, getStore);
```

### Component

```javaScript
// 有使用到共用的 function 或 state 要使用下面方式
<Component {...props}>
```
