# JavaScript

- [JavaScript](#javascript)
  - [常用變數](#常用變數)
  - [重組字串](#重組字串)
  - [Function](#function)
  - [判斷](#判斷)
    - [是否為空或存在](#是否為空或存在)
    - [常用運算子](#常用運算子)
    - [Optional Chaining 和 Nullish Coalescing](#optional-chaining-和-nullish-coalescing)
    - [雙驚嘆號的作用](#雙驚嘆號的作用)
  - [物件](#物件)
  - [陣列](#陣列)
  - [迴圈](#迴圈)
    - [ForEach](#foreach)
    - [Find](#find)
    - [Filter](#filter)
  - [Click 預設事件，終止函數運行](#click-預設事件終止函數運行)
  - [時間](#時間)
  - [解構並指定變數](#解構並指定變數)
  - [轉換](#轉換)
    - [轉整數](#轉整數)
    - [String to number](#string-to-number)
  - [Console](#console)
    - [群組](#群組)
  - [註解 JSDoc](#註解-jsdoc)
  - [測試推播](#測試推播)

## 常用變數

- POST : params
- GET: qs, query

**[⬆  back to top](#javascript)**

## 重組字串

- join()

```js
const demo = ['title1', 'title2', 'title3'];

console.log(demo.join(' / ')); // title1 / title2 / title3
```

[擷取字串](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substring)

**[⬆  back to top](#javascript)**

## Function

- 動態參數

```js
// ..args ->之後帶的參數都會在第三個位置
const app ＝ (method0, uri, ...args) => {

}
```

**[⬆  back to top](#javascript)**

## 判斷

### 是否為空或存在

```js
if (Object.entries(qs).length === 0) {} // 如果物件為空
if (data.length > 0) {} // 如果是空陣列
!!Number(value) // 0.00 強制轉型判斷是否存在
```

**[⬆  back to top](#javascript)**

### 常用運算子

減少使用判斷的做法是存成物件方式來代替

- 注意一元表達式盡量別寫在function裡，除非有用const，因為他是一個變數
- 判斷要語意化邏輯清楚，不能太多層，第一直覺未看得出來就不ＯＫ，注意開關判斷是否正常

> ||

1. 只要 || 前面為 true,不管 || 後面是true還是false，都返回 || 前面的值。
1. 只要 || 前面為 false,不管 || 後面是true還是false，都返回 || 後面的值。

| 前面 true | 返回前面的值 | 前面 false | 返回後面的值 |
| ---- | ----  | ---- | ----  |
| `alert(true || true)` | true | `alert(false || true)` | true |
| `alert(true || false)` | true | `alert(false || false)` | false |
| `alert(true || '')`  | true | `alert(false || '')`  | '' |
| `alert(true || undefined)` | true | `alert(false || undefined)` | undefined |

> &&

1. 只要 && 前面是 true，無論 && 後面是 true 還是 false，結果都將返 && 後的值。
1. 只要 && 前面是 false，無論 && 後面是 true 還是 false，結果都將返 && 前面的值。

| 前面 true | 返回後面的值 | 前面 false | 返回後面的值 |
| ---- | ----  | ---- | ----  |
| `alert(true && true)` | true | `alert(false && true)` | false |
| `alert(true && false)` | false | `alert(false && false)` | false |
| `alert(true && '')`  | '' | `alert(false && '')`  | false |
| `alert(true && undefined)` | undefined | `alert(false && undefined)` | false |

```js
ext.stats && ext.stats.favor || 0  // && 為優先權會先處理所以括弧位置要如下
(ext.stats && ext.stats.favor) || 0
```

[js運算符 && 與 || 的用法](https://www.itread01.com/content/1505121610.html)

### Optional Chaining 和 Nullish Coalescing

- Optional Chaining 使用「以回傳 undefined代替拋出錯誤」的概念來精簡程式碼：

- 從普通的 dot notation 取值改成 ?. 後，當運算子左邊的值並非 null 或 undefined 時，才會繼續往右手邊取值下去，否則便直接回傳 undefined 。

```js
const authorName = article?.author?.name;
```

- Nullish Coalescing 語法定義了一個運算子 ??：當運算子的左手邊 (left-hand side, LHS) 值為 null 或 undefined 的話，便會回傳右手邊 (right-hand side, RHS) 值。

```js
const itemHeight = itemHeight ?? 300;
```

[Optional Chaining 和 Nullish Coalescing](https://medium.com/%E7%A8%8B%E5%BC%8F%E7%8C%BF%E5%90%83%E9%A6%99%E8%95%89/%E4%BE%86%E8%AB%87-javascript-%E7%9A%84-optional-chaining-%E5%92%8C-nullish-coalescing-part-i-992625a1861d)

### 雙驚嘆號的作用

- !! 強制轉型 讓 undefind 或 null 直接變成布林
- 驚嘆號(!)是個邏輯運算符，名稱為”Logic NOT”，用在布林值上具有反轉(Inverted)的功能，雙驚嘆號(!!)就等於”反轉再反轉“，等於轉回原本的布林值:

```js
const aBool = true
const bBool = !aBool // false
const cBool = !!aBool // true
```

- 雙驚嘆號(!!)並不單純是在這樣用的，它是為了要轉換一些可以形成布林值的情況值，列出如下:

1. false: 0, -0, null, false, NaN, undefined, ''(空白字串)
1. true: 不是 false 的其他情況

```js
const aBool = !!0 // false
const bBool = !!'false' // true
const cBool = !!NaN // false
```

- 經過雙驚嘆號運算後，只會很單純出現 true 和 false 兩種，可以單純化減少某些特別情況時的出錯機會。

> 例如希望'' 和 null 被視為完全相同時:

```js
const a = ''
const b = null

a === b // false
!!a === !!b // true
```

**[⬆  back to top](#javascript)**

## 物件

- 取出物件需要用map等方式取出。

```js
Object.keys(qs)      // 取 key
Object.values(qs)  // 取 值
```

Ob.value 物件給值時，如果setState放前面也會被影像到，原因可能是淺層複製的專係

**[⬆  back to top](#javascript)**

## 陣列

| 分類 | 方法 |
| ---- | ----  |
| 會改變原始陣列 | push()、pop()、shift()、unshift()、reverse()、splice()、sort()、copyWithin()、fill() |
| 回傳陣列元素資訊或索引值 | length、indexOf()、lastIndexOf()、find()、findIndex()、filter() |
| 針對每個元素處理 | forEach() |
| 產生新的陣列或新的值 | join()、concat()、slice()、map()、reduce()、reduceRight()、flat()、flatMap()、Array.from()、Array.of()、toString() |
| 判斷並回傳布林值 | every()、some()、includes()、Array.isArray() |
| 其他用法 | keys()、valueOf() |

[各種陣列](https://www.oxxostudio.tw/articles/201908/js-array.html)

## 迴圈

### ForEach

- 對象是Ｏbject，簡化了 for loop。

```js
Object.keys(a).forEach(function (key){
    console.log(a[key]);
});
```

- 對象是Ａrray。

1. item - 物件。
1. index - 索引。
1. array - 陣列本身。

```js
any.forEach(function(item, index, array) {
console.log(item, index, array);
});
```

```js
newaaaa['level_name']="";
outGetLevel.ret.forEach(v => {
  newaaaa['level_name'] = v.level_id.toString() === newaaaa['level_id '].toString() ? v.level_name : newaaaa['level_name'] ;
});
```

- 陣列裡面是物件，要取某個物件。

```javascript
aa = [
  { a: 1 },
  { b: 2 },
  { c: 3 },
]
aa.forEach((v) => {
  console.log(v.a);
});
```

### Find

```js
outGetLevel.ret.find((i) => {
  if (i.level_id.toString() === newOut.level_id.toString()) {
    newOut.leve_name = i.level_name;
  }
  return newOut;
});
```

### Filter

- 物件對物件篩選出新的物件

```js
  const langs = [{
      key: 'en',
      text: 'English',
      image: { avatar: true, src: En },
    },{
      key: 'ja',
      text: '日本語',
      image: { avatar: true, src: Ja },
    },{
      key: 'vi',
      text: 'Vietnam',
      image: { avatar: true, src: Vi },
    }
  ];

  const config = ['en', 'ja'];

let settingLang = config ? langs.filter(v => config.locales.indexOf(v.key) !== -1 ) :  [] ;
```

[Object.keys()](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)

[How to loop through object in JavaScript](https://dev.to/saigowthamr/how-to-loop-through-object-in-javascript-es6-3d26)

[JavaScript 陣列20種操作的方法](https://hsiangfeng.github.io/javascript/20190421/1216566123/)

**[⬆  back to top](#javascript)**

## Click 預設事件，終止函數運行

```js
  // 終止預設行為
  event.preventDefault();
  // 終止事件傳導
  event.stopPropagation();
```

> function (wrapStyle)

```js
/**
 * 複製文字
 * @param {String} wrapStyle
 */
```

**[⬆  back to top](#javascript)**

## 時間

- 取得現在時間

```js
var today = new Date();
```

- 比較時間大小

```js
console.log((Date.parse(today)).valueOf());
```

**[⬆  back to top](#javascript)**

## 解構並指定變數

```js
const { show_promotion: showPromotion } = user;
```

**[⬆  back to top](#javascript)**

## 轉換

### 轉整數

```js
parseInt(string, radix)

// radix
// 可选。表示要解析的数字的基数。该值介于 2 ~ 36 之间。
// 如果省略该参数或其值为 0，则数字将以 10 为基础来解析。如果它以 “0x” 或 “0X” 开头，将以 16 为基数。
// 如果该参数小于 2 或者大于 36，则 parseInt() 将返回 NaN。
```

### String to number

```js
parseFloat(str)
parseInt(str [, radix])
```

[parseInt 和 parseFloat 函數](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Obsolete_Pages/Obsolete_Pages/Obsolete_Pages/%E9%A0%90%E5%85%88%E5%AE%9A%E7%BE%A9%E7%9A%84%E5%87%BD%E6%95%B8/parseInt_%E5%92%8C_parseFloat_%E5%87%BD%E6%95%B8)

## Console

### 群組

```js
    console.group('== 3');
    console.log('qs ', qs);
    console.log('post ', post);
    console.log('attaches ', attaches);
    console.groupEnd();
```

**[⬆  back to top](#javascript)**

## 註解 JSDoc

1. 開頭小寫
1. Type 大駝峰 @typedef
1. 如原本就已知型別就不用特別註明，只需要 //

> props

```js
/**
* @typedef PropsData
* @prop {boolean} isShow 顯示
* @prop {string} theme 主題樣式
*/

/**
 * 複製文字
 * @param {PropsData} props
 */
```

> onClick

```js
/**
 * @param {Function} onClick
*/
```

> return component

```js
/**
 * @returns {ReactElement} JSX
*/
```

```js
  /**
    * 搜尋條件篩選
    * @param {Event} ev event
    * @param {{
    * 'name': string,
    * value': (string|number),
    * }} params
    * name: 欄位名
    * value: 欄位值
    */
  const handleSearch = (ev, { name, value }) => {
  };
```

> object key 為變動

```js
  Object.<string, *>
=>  Object.<string, data>
```

**[⬆  back to top](#javascript)**

## 測試推播
```
window.dispatchEvent(new CustomEvent('notice', { detail: { message: { content: "M_WS_MANUAL_MONITOR",
text: "M_WS_MANUAL_MONITOR", type: "manual_monitor", front: '測試', end:'11111' }, event: 'notice' } }))
```

## CSV

> 匯出 CSV 換行
```
\u2028 \n
\u2029 \r
`${d.ip}\u2028RexTest`
```