# <font color="#04dcff">Git 流程</font>
`1. 設定 git 設定`
```git
git init
```
`2. 把檔案交給 Git`
```
git add 檔案名稱
```
`3. 推送至git檔案庫`
```
git commit -m '修改敘述'
```
`4. 新增遠端儲存庫`
```
git remote add origin git@URL
```
`5. 推送本地的 master 分支到 origin 遠端版本庫，同時遠端的分支也是叫做 master。`
```
git push origin master
```

# <font color="#04dcff">使用的遠端資料</font>
`抓取遠端資料。`
```
git clone
```
`讀取遠端是否連線。`
```
ssh
```
`顯示 Git 用來讀寫遠端簡稱時所用的網址。`
```
git remote -v
```
# <font color="#04dcff">vim 指令</font>
1. : 代表接下來為指令。
1. w 代表寫入 = 儲存。
1. q 代表離開程式。
1. !  代表強制執行。

# <font color="#04dcff">分支</font>
### <font color="#04dcff">新增/刪除分支</font>
```
1. git branch master2 在本端建立分支。
```
```
2. git push origin master2 推送至遠端並指定分支。
```
```
3. git branch -d <branch> 刪除本地分支。
```

### <font color="#04dcff">查詢分支</font>
```
git branch -a 查詢遠端分支。
```
```
git branch 查詢本端分支。
```
```
git remote update -p 強制更新遠端分支。
```
```
tig 分支圖
```

# <font color="#04dcff">Log</font>
### <font color="#04dcff">檢視紀錄</font>
```
git log 顯示所有紀錄。
```
```
git log --oneline 顯示簡略紀錄。
```
```
git log --graph --oneline 顯示 id 與 commit 內容。
```
```
git log --graph --oneline --decorate --all --color 改顏色。
```
```
git log 檔案 顯示單一檔案的紀錄。
```
```
git log -p 顯示每次commit做了什麼修改。
```

### <font color="#04dcff">查詢紀錄</font>
`查詢建置人，|為"或"的意思。`
```
git log --oneline --author="建置人 | 建置人"
```
`查詢commit含的內容文字。`
```
git log --oneline --grep="commit 內容文字"
```
`查詢commit檔案含有內容的文字。`
```
git log --oneline --S "檔案內容含的文字
```
`查詢特定時間的紀錄。`
```
git log --oneline --since="9am" --until="12am" --after="2019-07"
```
`查詢修改的內容`
```
git show commitid
```
`查看分支`
```
git log --oneline --graph --color --decorate --all
```

# <font color="#04dcff">reset</font>

`查看所有訊息版本`
```
git reflog
```
`回復到最新提交版本`
```
git reset --hard HEAD
```
`等於 ~1 回復到上一個提交版本`
```
git reset --hard HEAD~
```
`n 等於往上第幾個提交版本 回復之前指定的提交版本`
```
git reset --hard HEAD~n
```
`根據 commit id 回覆到指定版本`
```
git reset --hard commit_id
```
# <font color="#04dcff">檔案移除</font>
1. rm 檔案名稱 -> 刪除檔案。
1. rm 資料夾名稱 -r -f -> 。
1. git rm welcome.html -> 刪除檔案後並加入暫存區。
1. git rm welcome.html --cached  -> 移除資料並不讓git控管，這樣才能 add 跟 commit。

# <font color="#04dcff">常用快速鍵</font>
[常用快速鍵](https://git-scm.com/book/zh-tw/v1/Git-%E5%9F%BA%E7%A4%8E-%E6%8F%90%E7%A4%BA%E5%92%8C%E6%8A%80%E5%B7%A7/)
```
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.lg log --graph --decorate --oneline --color --all
git config --global alias.line log --oneline --graph --decorate
git config --global alias.update remote update -p origin
```

# <font color="#04dcff">儲藏 (Stashing)</font>
```
git stash save "名稱" 暫時儲存現狀的操作
```
```
git stash list 顯示暫存清單
```
```
git stash pop 恢復暫存的操作
```
```
git stash drop 刪除暫存的操作
```
```
git stash clear 刪除所有暫存的操作
```