# Jest

- [Jest](#jest)
  - [測試頁面](#測試頁面)
  - [測試常見名詞介紹](#測試常見名詞介紹)
  - [describe](#describe)
  - [it , test](#it--test)
  - [Expect](#expect)
  - [Mock](#mock)
  - [Snapshot](#snapshot)
  - [資料來源由外部傳入](#資料來源由外部傳入)
  - [測試注意的地方](#測試注意的地方)
  - [container vs baseElement: el](#container-vs-baseelement-el)

## 測試頁面

- 顯示報告

```bash
# 詳細路徑
npm test -- --coverage src/js/about/__tests__/name.test.js
npm test -- --coverage name.test.js
# 監聽狀態
npm test -- --coverage name.test.js --watch
```

- 不顯示報告

```bash
# 詳細路徑
npm test src/js/about/__tests__/name.test.js
npm test name.test.js
# 監聽狀態
npm test -- name.test.js --watch
```

**[⬆ back to top](#測試頁面)**

## 測試常見名詞介紹

| 專有名詞 | 說明  |
| ---- | ----  |
| Test Runner:  | 可以執行單元測試，並執行他們，最後輸出測試結果。如Mocha, Jasmine, Jest, AVA。 |
| Assertion Library:  | 斷言庫，可驗證測試的結果，如Chai, Should, Expect。 |
| Mocks:  | 當程式中有許多相依性時，使用stubs或mocks來模擬邏輯。前者模擬黑箱物件，後者則提供許多特性供測試使用。 |
| Mocking library: | 實行mocks來模擬單元測試。如Sinon, TestDouble。 |

**[⬆ back to top](#測試常見名詞介紹)**

## describe

- describe中通常寫一個元件或是一個function。
- 將相關的測試案例整合起來定義一個測試結果(test suite)，可以使用beforeEach，
- afterEach決定再跑測試之前或之後要先執行的區塊。
- Test Suites的數字就是describe的數量。

**[⬆ back to top](#describe)**

## it , test

- 定義一個最小的測試案例(test case)。
- Tests的數字就是describe的數量。
- it是test的alias，所以兩個是一樣的東西。
- 做單一測試

```js
it.only (() => {

})
```

**[⬆ back to top](#it--test)**

## Expect

- 用來判斷是否和預期值相同的斷言庫。

[Expect 匹配器表](https://jestjs.io/docs/en/expect/)

| Jest 常用匹配器 | 說明  |
| ---- | ----  |
| toBe | 比較兩物件是否有相同的值，常用來比較數值。 |
| toEqual | 比較兩物件是否有相同的值。 |
| toBeDefined | 確認物件是否已被定義。 |
| toBeNull | 只匹配null。 |
| toBeUndefined | 只匹配undefined。 |
| toBeTruthy | 匹配任何 if 語句為真。 |
| toBeFalsy | 匹配任何 if 語句為假。 |
| toBeCalled | 檢查mock函示是否被呼叫。 |
| jest.fn() | 模擬一個mock的函示。 |
| jest.mock() | 讓測試專注在現在測試的模組本身，mock 掉 import 進來的東西。 |
| jest.resetModules() | 確保 import/require 的 module 是初始乾淨未被污染的狀況。 |
| jest.resetAllMocks() | 重設所有 mock 物件的狀態。 |
| toMatchSnapshot | 產生快照，會在 __test__資料夾下多產生一個的 __snapshots__的資料夾下。 |
| toBeCalledWith | 偵測是否觸發了某個 function，並夾帶哪些參數。 |
| toContain | 確認項目是否包含在一陣列中。 |
| toBeInTheDocument | 是否正確被render 使用於非同步 |

[jest-dom - 套件](https://github.com/testing-library/jest-dom/)

| jest-dom 常用匹配器 | 說明  |
| ---- | ----  |
| toHaveClass | 含有的 class 名稱。 |
| toHaveStyle | 含有style屬性。 |
| toHaveTextContent | 內容含有的文字。  |
| toBeDisabled | 表單物件是否被進用。 |
| toHaveValue | 表單value內的值。 |
| toBeChecked |  checkobx 是否被點選。 |
| toContainHTML | 含有的html 內容 |

- toContain

```js
const shoppingList = [
  'diapers',
  'kleenex',
  'trash bags',
  'paper towels',
  'beer',
];

it('the shopping list has beer on it', () => {
  expect(shoppingList).toContain('beer');
});
```

**[⬆ back to top](#expect)**

## Mock

- mock 系統時間

```js
Date.now = jest.fn(() => 1602324702229);
```

- 測試 alert or window.open 等 window物件得用 mock 方式測試。

```js
window.alert = jest.fn();

expect(window.alert).toHaveBeenCalled(); -->測試是否有被呼叫。
```

- jest.fn()
- 必須寫在最外層，寫在物件裡會沒作用

```js
it('call a mock function', () => {
  const mockFunc = jest.fn();
  mockFunc();
  expect(mockFunc).toBeCalled();
});
```

**[⬆ back to top](#mock)**

## Snapshot

- toMatchSnapshot

welcome.js

```js
export default class Welcome extends Component {
  render() {
    return (
      <div>Hello world!</div>
    );
  }
}
```

welcome.test.js

```js
import React from 'react';
import renderer from 'react-test-renderer';
import Welcome from '../src/containers/welcome';
describe('Welcome (Snapshot)', () => {
  it('Welcome renders hello world', () => {
    const component = renderer.create(<Welcome />);
    const json = component.toJSON();
    expect(json).toMatchSnapshot();
  });
});
```

welcome.test.js.snap

```js
exports[`Welcome (Snapshot) Welcome renders hello world 1`] = `
<div>
  Hello world!
</div>
```

**[⬆ back to top](#snapshot)**

## 資料來源由外部傳入

> 當資料來源由外部傳入時使用 rerender 來更新外部資料

```js
const props = {
  qs: {}
};

/* 一開始 Render */
const result = render(
  <ApiContext.Provider>
    <Component {...props} />
  </ApiContext.Provider>,
);

const { rerender } = result;
const newProps = {
  ...props,
  qs: { aa: 1, bb: 2},
};

/* 中間資料更新 Render */
rerender(
  <ApiContext.Provider>
    <Component {...newProps} />
  </ApiContext.Provider>,
);
```

**[⬆ back to top](#資料來源由外部傳入)**

## 測試注意的地方

- 發現 mock api 無法載入資料時的問題排解
  1. 先註解其他測試飯是否是被其他mock影響。
  2. 先註解其他測試看是否被覆蓋。
  3. mockApi 是否需要帶入值， query(true) 或 query({})。
  4. 檢查 mock log 出來的 url 是否跟預期的一樣逐步檢查。
  5. 調換順序，有可能mockapi的順序問題。
  6. 無法順利載入資料時注意異步問題， async 和 await是否需要帶入。
  7. mock api時載入的資料都會同一個mock，如果需要做到更換搜尋條件後的結果是變更條件後的結果時就得再另外mock api。
  8. 順序:先將所有資料都抓取到後再做判斷。

- 發現 mock api 載入資料時資料一直是舊資料
  1. 先註解其他測試飯是否是被其他mock影響。
  2. 確認是否有清除上一個 mock。

- 清除上一個 api資料

```js
afterEach(() => {
  nock.cleanAll();
});
```

- 異步問題
    1. 當使用非同步時執行mock api 回來後才執行 waitFor() 因為它需要等待api執行完成後才執行 waitFor() 裡的內容

```js
querySelector 抓取只會抓一次(一開始載入時)，並不會重複抓取，

awit 等待程式執行完再往下跑，如api，

wait() 像是迴圈一樣 一直在function裡面執行等合乎條件後才會return出去。

await wait(() => console);

等於

await wait( () => {
  return console;
})
```

- 注意以下狀況不是用單引號。

```js
不是單引號:
'/api/v1/auto/${id}/detail_result'

而是``
`/api/v1/auto/${id}/detail_result`
```

- 注意傳遞的資料型態是否正確。

- 取得 item 數量。

```js
await wait(() => expect(el.querySelectorAll('.report-table tbody tr').length).toBe(3));
```

- 需確定每個帶入 component 的變數是否有正確顯示尤其是使用 JSON.parse(JSON.stringify(props))

**[⬆ back to top](#測試注意的地方)**

## container vs baseElement: el

- contaner render: 出來的元素只有當下測試元件的第一層
- baseElement: el: render 出來的元件為當下測試元件的第一層與因當下元件呼叫的元件層，例如 modal，debug 預設render出來的為此範圍

**[⬆ back to top](#container-vs-baseelement-el)**
