# React

- [React](#react)
  - [選套件套件參考條件](#選套件套件參考條件)
  - [值要存放變數還是state](#值要存放變數還是state)
  - [正確的使用state](#正確的使用state)
  - [事件處理](#事件處理)
  - [class component換function component 要注意的地方](#class-component換function-component-要注意的地方)
  - [物件塞入新值](#物件塞入新值)
  - [Effect](#effect)
  - [自定義屬性](#自定義屬性)
    - [取得自定義屬性值](#取得自定義屬性值)
  - [顯示字串](#顯示字串)
  - [Render HTML](#render-html)
  - [Function Component status](#function-component-status)
  - [判斷](#判斷)
  - [雷](#雷)
  - [翻譯](#翻譯)

## 選套件套件參考條件

1. 固定維護
1. 使用人數高
1. 不要用原生JS

## 值要存放變數還是state

1. API一定要使用state做存放資料的方式，不能使用變數不然會影響到生命週期，因為一開始為空載入後才換成API 所傳回來的值，這就已經構成變動。
1. 如果值是從頭到尾都不會變動到的才能使用變數作為存放。

## 正確的使用state

- State 的更新可能是非同步的，因為 this.props 和 this.state 可能是非同步的被更新，你不應該依賴它們的值來計算新的 state。

- 錯誤

```js
this.setState({
  counter: this.state.counter + this.props.increment,
});
```

- 正確

```js
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```

- or

```js
this.setState(function(state, props) {
  return {
    counter: state.counter + props.increment
  };
});
```

## 事件處理

1. 事件的名稱在 React 中都是 camelCase，而在 HTML DOM 中則是小寫。
1. 事件的值在 JSX 中是一個 function，而在 HTML DOM 中則是一個 string。

- html

```html
<button onclick="activateLasers()">Activate Lasers/button>
```

- React

```js
<button onClick={activateLasers}>Activate Lasers</button>
```

- 取得元素中的文字

```js
e.target.textContent
```

- 取得input 中的值

```js
e.target.value
```

- 在 React 中，你不能夠在像在 HTML DOM 中使用 return false 來避免瀏覽器預設行為。你必須明確地呼叫 preventDefault。 將參數傳給 Event Handler，以下兩種皆可。

```js
<button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>
<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
```

## class component換function component 要注意的地方

1. 使用原本變數宣告如果更換變數內容沒更換要注意是否另外複製變數再塞回去。
2. 在 useEffect 使用 setState 會出現無法載入內容的問題。

## 物件塞入新值

- {object}.value 但在 react 的 state 裡這樣做更動了他不會即時更新而使用 setState才會及時更新。

> 注意作 function 時，預設變數如果是status的話可能會有無法正確傳到值的問題，status就由外面導入

```js
const getExecutionLog = async (newQuery = query, newPagination = pagination)
```

## Effect

- 首頁載入只刷一次迴圈後就停止Render

```js
  useEffect(() => {
    data.forEach(() => {});
  }, [data]);
```

- State 在 effect 裡抓不到更新值的方法
- 以下方式只會執行一次

```js
Object.keys(opcode).length  //--> 判斷物件是否為空
init //--> 當作開關，第一次時為true會執行但第二次為false就不會再執行一次。

  useEffect(() => {
    if (init && Object.keys(opcode).length) {
      getEntries();
      handleOpcodeChangeByCategory('', false);
      setInit(false);
    }
  }, [opcode]);
```

## 自定義屬性

- 自定義屬性
- 使用 data- 開頭

[How to access custom attributes from event object in React?](https://stackoverflow.com/questions/20377837/how-to-access-custom-attributes-from-event-object-in-react)

### 取得自定義屬性值

- function component
'e.target.getAttribute("data-index")'

- class component
'e.target.data-index'

[Get Key Index on Click ES6 React](https://stackoverflow.com/questions/40044861/get-key-index-on-click-es6-react)

## 顯示字串

```js
{`${cash.currency} 字串 ${cash.balance}`}
```

## Render HTML

```js
<div dangerouslySetInnerHTML={{ __html: yourhtml }} />
```

[How to render a HTML string in React?](https://stackoverflow.com/questions/47483964/how-to-render-a-html-string-in-react)

## Function Component status

state  在function裡面是全部都執行完才會存入state，所以要把資料都處理完後在放state

## 判斷

- react jsx inline if else altering style value

```js
<div style={isMarginNeeded ? {marginTop:10} : {}} />
```

## 雷

- input type 不要用 number 應該是semetic 的問題，有些人的電腦會噴錯

## 翻譯

- I18n

```js
import { sprintf } from 'sprintf-js';
import I18n from 'lang';

sprintf(I18n('語系代碼'), value)
```

- 輸出HTML格式

```js
<span dangerouslySetInnerHTML={{ __html: sprintf(I18n(label), count, total_amount) }} />
```
