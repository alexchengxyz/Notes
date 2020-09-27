# Git 常用指令

## 目錄

1. [流程](#流程)
1. [使用的遠端資料](#使用的遠端資料)
1. [流程](#流程)
1. [使用的遠端資料](#使用的遠端資料)
1. [vim 指令](#vim指令)
1. [分支](#分支)
1. [Log](#log)
1. [reset](#reset)
1. [檔案移除](#檔案移除)
1. [常用快速鍵](#常用快速鍵)
1. [儲藏(Stashing)](#儲藏-stashing)

## 流程

1. 設定 git 設定
1. 把檔案交給 Git
1. 推送至 git 檔案庫
1. 新增遠端儲存庫
1. 推送本地的 master 分支到 origin 遠端版本庫，同時遠端的分支也是叫做 master。

```git
git init
git add 檔案名稱
git commit -m '修改敘述'
git remote add origin git@UR
git push origin master
```

**[⬆ back to top](#目錄)**

## 使用的遠端資料

- 抓取遠端資料。

```git
git clone
```

- 讀取遠端是否連線。

```git
ssh
```

- 顯示 Git 用來讀寫遠端簡稱時所用的網址。

```git
git remote -v
```

**[⬆ back to top](#目錄)**

## vim 指令

1. : 代表接下來為指令。
1. w 代表寫入 = 儲存。
1. q 代表離開程式。
1. ! 代表強制執行。

**[⬆ back to top](#目錄)**

## 分支

### 新增/刪除分支

- 在本端建立分支。

```git
git branch master2
```

- 推送至遠端並指定分支。

```git
git push origin master2
```

- 刪除本地分支。

```git
git branch -d <branch>
```

### 查詢分支

- 查詢遠端分支。

```git
git branch -a
```

- 查詢本端分支。

```git
git branch
```

- 強制更新遠端分支。

```git
git remote update -p

```

- 分支圖

```git
tig
```

**[⬆ back to top](#目錄)**

## Log

### 檢視紀錄

- 顯示所有紀錄。

```git
git log
```

- 顯示簡略紀錄。

```git
git log --oneline
```

- 顯示 id 與 commit 內容。

```git
git log --graph --oneline
```

- 改顏色。

```git
git log --graph --oneline --decorate --all --color
```

- 顯示單一檔案的紀錄。

```git
git log 檔案
```

### 查詢紀錄

- 查詢建置人，|為"或"的意思。

```git
git log --oneline --author="建置人 | 建置人"
```

- 查詢 commit 含的內容文字。

```git
git log --oneline --grep="commit 內容文字"
```

- 查詢 commit 檔案含有內容的文字。

```git
git log --oneline --S "檔案內容含的文字
```

- 查詢特定時間的紀錄。

```git
git log --oneline --since="9am" --until="12am" --after="2019-07"
```

- 查詢修改的內容

```git
git show commitid
```

- 查看分支

```git
git log --oneline --graph --color --decorate --all
```

**[⬆ back to top](#目錄)**

## reset

- 查看所有訊息版本

```git
git reflog
```

- 回復到最新提交版本

```git
git reset --hard HEAD
```

- 等於 ~1 回復到上一個提交版本

```git
git reset --hard HEAD~
```

- n 等於往上第幾個提交版本 回復之前指定的提交版本

```git
git reset --hard HEAD~n
```

- 根據 commit id 回覆到指定版本

```git
git reset --hard commit_id
```

**[⬆ back to top](#目錄)**

## 檔案移除

1. rm 檔案名稱 -> 刪除檔案。
1. rm 資料夾名稱 -r -f -> 。
1. git rm welcome.html -> 刪除檔案後並加入暫存區。
1. git rm welcome.html --cached -> 移除資料並不讓 git 控管，這樣才能 add 跟 commit。

**[⬆ back to top](#目錄)**

## 常用快速鍵

[常用快速鍵](https://git-scm.com/book/zh-tw/v1/Git-%E5%9F%BA%E7%A4%8E-%E6%8F%90%E7%A4%BA%E5%92%8C%E6%8A%80%E5%B7%A7/)

```git
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.lg log --graph --decorate --oneline --color --all
git config --global alias.line log --oneline --graph --decorate
git config --global alias.update remote update -p origin
```

**[⬆ back to top](#目錄)**

## 儲藏 Stashing

- 暫時儲存現狀的操作

```git
git stash save "名稱"
```

- 顯示暫存清單

```git
git stash list
```

- 恢復暫存的操作

```git
git stash pop
```

- 刪除暫存的操作

```git
git stash drop
```

- 刪除所有暫存的操作

```git
git stash clear
```
