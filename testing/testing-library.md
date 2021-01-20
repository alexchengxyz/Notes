# Testing Library

## 簡介

### render

react-testing-library 的 render 將所有的子組件都 render 出來成為 DOM 節點。

### getByTestId 、 getByText

render 後會回傳的 Method ，兩個都是用來搜尋 DOM ， getByTestId 是以 DOM 中的 data-testid 值取要斷言的 DOM ， getByText 則是以該 DOM 內呈現的內容，獲取到 DOM 後便能以 textContent 再取得內容。

### container

- container 也是 render 所回傳的，等於取得整包 DOM 物件，甚至是能夠直接對它使用 query​Selector 來搜尋節點，通常我會在搞不清楚到底 Render 了什麼的時候，用 innerHTML 來偷看 😆。
- render 出來的元素就是整個body 如果元素本身不是整頁就會抓不到(因為無body)

### fireEvent

這個 Method 可以觸發 DOM 的事件，例如 onClick 、 onChange 等等。

### 開始測試

其實只要了解上述幾個簡單的 API ，就能夠輕鬆對 Component 的節點做測試，下方先 render 出 Counter ，並對 span 的內容做斷言，確認是否 render 正確：

```js
import React from 'react';
import { render, fireEvent, cleanup } from 'react-testing-library';
import Counter from '../src/component/Countera/Counter';

describe('Test <Counter />', () => {
  // 每次測試後將 render 的 DOM 清空
  afterEach(cleanup);
  test('測試是否正常 render ', () => {
    // render Component
    const { getByTestId, getByText, container, } = render(<Counter />);

    // 下方三個方法都可以找到顯示計數的 <span />
    expect(getByTestId('display_count').textContent).toBe('點了0下');
    expect(getByText('點了0下').textContent).toBe('點了0下');
    expect(container.querySelector('span').innerHTML).toBe('點了0下');
  });
});
```

## 常用抓取元素

- 抓取元素時要注意，如抓表單元素class太多不好抓建議抓 name 屬性(不會有重複問題)。

[Queries](https://testing-library.com/docs/dom-testing-library/api-queries/)
[Cheatsheet](https://testing-library.com/docs/dom-testing-library/cheatsheet/#queries/)

| 常用抓取元素 | 說明  |
| ---- | ----  |
| document.querySelector() | 抓取class。 |
| querySelector | 抓取單一元素。 |
| querySelectorAll | 抓取相同多個元素。 |
| parentNode | 取得元素上層。 |

- debug

```js
import React from 'react'
import { render } from '@testing-library/react'

const HelloWorld = () => <h1>Hello World</h1>
const { debug } = render(<HelloWorld />)
debug()
```

- 查詢內容，顯示 html

```js
expect(container.querySelector('.ext-dialog-wrap')).innerHTML;
```

- 檢查圖片

```js
it('取得第三方應用預覽圖', () => {
  const { baseElement: el, } = result;
  expect(el.querySelector('img')).toHaveAttribute('src', '/image/ext/frontside_set.jpg');
});
```
