## tsconfig.node.json 和 tsconfig.app.json 差異
它們的目的是為了分別配置 Node.js 環境和 Vue.js 應用程序的 TypeScript 編譯。

## tsconfig.node.json
目的： tsconfig.node.json 通常用於配置 Node.js 環境下的 TypeScript 編譯選項。

### 主要選項：

1. target：指定生成的 JavaScript 代碼的 ECMAScript 目標版本。
1. module：指定生成的模塊代碼的模塊系統，通常是 "commonjs"。
1. moduleResolution：指定模塊解析策略，通常是 "node"。
1. outDir：指定 TypeScript 編譯器的輸出目錄。
1. rootDir：指定項目的根目錄。
1. types：引入的 TypeScript 定義文件，可能包括 "node"。

## tsconfig.app.json
目的： tsconfig.app.json 主要用於配置 Vue.js 應用程序的 TypeScript 編譯選項。

### 主要選項：

1. target：指定生成的 JavaScript 代碼的 ECMAScript 目標版本。
1. module：指定生成的模塊代碼的模塊系統，通常是 "esnext"。
1. moduleResolution：指定模塊解析策略，通常是 "node"。
1. strict：啟用所有嚴格類型檢查選項。
1. esModuleInterop：啟用對 import/export 的互通性支持。
1. skipLibCheck：是否跳過對宣告文件的檢查。
1. forceConsistentCasingInFileNames：強制在文件名中使用一致的大小寫。
1. outDir：指定 TypeScript 編譯器的輸出目錄。
1. rootDir：指定項目的根目錄。

types：引入的 TypeScript 定義文件，可能包括與 Vue.js 相關的類型。
總的來說，tsconfig.node.json 主要用於配置 Node.js 環境的 TypeScript 編譯，而 tsconfig.app.json 主要用於配置 Vue.js 應用程序的 TypeScript 編譯。兩者的區別在於它們所針對的環境和應用類型不同。






