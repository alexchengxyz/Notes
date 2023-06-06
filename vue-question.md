# Vue 坑

## local-storage 顯示 ReferenceError: global is not defined

```js
// 僅在瀏覽器環境中條件式匯入 local-storage
if (typeof window !== 'undefined') {
  const ls = require('local-storage');

  watch(locale, (newLocale) => {
    ls.set<string>('lang', newLocale);
    console.log(111);
  });
}
```
or
```js
import { watch, onMounted } from 'vue';

onMounted(() => {
  watch(locale, (newLocale) => {
    localStorage.setItem('lang', newLocale);
  });
});

```
