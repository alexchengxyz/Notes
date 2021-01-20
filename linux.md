# Linux指令

- [Linux指令](#linux指令)
  - [常用指令](#常用指令)
  - [檔案權限](#檔案權限)
  - [帳號切換](#帳號切換)
  - [yum](#yum)
  - [apt-get](#apt-get)
  - [Plugins](#plugins)
    - [Fish Shell](#fish-shell)
  - [推薦](#推薦)

## 常用指令

|  指令   | 說明
|  ----  | ----  |
| reboot | 重開機 |
| history  | 紀錄 |
| clear  |  | 清除
| mkdir  |  | 建立資料夾
| cp | 複製 |
| rm | 刪除 |
| rm -d | 刪除空目錄 |
| rm -rf | 刪除目錄和裡面檔案 |
| mv | 移動 |
| echo | 印出指令 |
| echo "語法" > sample.php | 新增一個php檔案內容 |
| cat fileName | 執行檔案 |
| pwd | 當前目錄位置 |
| ls | 列出目前目錄檔案 |
| ls -al | 列出目前目錄檔案細項 |
| ifconfig | 查詢網卡 |
| service network stop | 暫停網路 |
| service network start | 啟動網路 |
| ip addr show | 檢查IP |
| ifconfig | 檢查網卡 |
| netstat | 檢查目前使用的IP |
| grep -r 'extends' src/js輸入訊息 | 查看測試 |

**[⬆ back to top](#linux指令)**

## 檔案權限

1. 644 常見權限
1. 705 一般狀況

[Linux 將檔案分成三種身份、四種權限](http://s2.naes.tn.edu.tw/~kv/file.htm/)

**[⬆ back to top](#linux指令)**

## 帳號切換

1. login -f username root 用户切换为普通用户  - （加 -f 不用输入密码）例如普通用户的用户名为hadoop，这里就是 login -f hadoop
1. sudo su 普通用户切换为root用户

[Linux 將檔案分成三種身份、四種權限](http://s2.naes.tn.edu.tw/~kv/file.htm/)

**[⬆ back to top](#linux指令)**

## yum

- yum可以用於運作rpm包，例如在Fedora系統上對某個軟件的管理

```linux
yum install <package_name> 安裝
```

```linux
yum remove <package_name> 卸載
```

```linux
yum update <package_name> 更新
```

```linux
yum clean 清除己經完成安裝而不必要的暫存程式
```

```linux
yum search keyword 搜索
```

```linux
yum list 列出所有可安裝的軟件包
```

```linux
yum list updates 列出所有可更新的軟件包
```

```linux
yum list installed 列出所有已安裝的軟件包
```

```linux
yum list extras 列出所有已安裝但不在Yum Repository 內的軟件包
```

```linux
yum list <package_name> 列出所指定的軟件包
```

**[⬆ back to top](#linux指令)**

## apt-get

- apt-get可以用於運作deb包，例如在Ubuntu系統上對某個軟件的管理

```linux
apt-get install <package_name> 安裝
```

```linux
apt-get remove <package_name> 卸載
```

```linux
apt-get update <package_name> 更新
```

```linux
apt-cache search package 搜索包
```

```linux
apt-cache show package 獲取包的相關信息，如說明、大小、版本等
```

```linux
sudo apt-get install package 安裝包
```

```linux
sudo apt-get install package -- reinstall 重新安裝包
```

```linux
sudo apt-get -f install 修復安裝"-f = --fix-missing"
```

```linux
sudo apt-get remove package 刪除包
```

```linux
sudo apt-get remove package -- purge 刪除包，包括刪除配置文件等
```

```linux
sudo apt-get update 更新源
```

```linux
sudo apt-get upgrade 更新已安裝的包
```

```linux
sudo apt-get dist-upgrade 升級系統
```

```linux
sudo apt-get dselect-upgrade 使用dselect 升級
```

```linux
apt-cache depends package 了解使用依賴
```

```linux
apt-cache rdepends package 是查看該包被哪些包依賴
```

```linux
sudo apt-get build-dep package 安裝相關的編譯環境
```

```linux
apt-get source package下載該包的源代碼
```

```linux
sudo apt-get clean && sudo apt-get autoclean 清理無用的包
```

```linux
sudo apt-get check 檢查是否有損壞的依賴
```

**[⬆ back to top](#linux指令)**

## Plugins

### Fish Shell

- 語法亮亮
  1. 對於臨時： bash or fish 指令切換
  1. 永久性: chsh -s / bin / bash or chsh -s / usr / bin / fish

```linux
sudo yum-config-manager --add-repo https://download.opensuse.org/repositories/shells:fish:release:2/CentOS_7/shells:fish:release:2.repo
sudo yum install fish
```

[Fish shell：讓指令更接近懶人使用](https://noob.tw/fish-shell/)
[How to install, configure and use Fish Shell in Linux?](https://www.2daygeek.com/linux-fish-shell-friendly-interactive-shell/)

**[⬆ back to top](#linux指令)**

## 推薦

- 語法亮亮，方便提示字

[centos7安装zsh配置oh-my-zsh](https://www.jianshu.com/p/4ce7d511bc13/)
[centos7 安装zsh和oh-my-zsh](https://www.jianshu.com/p/fa82d932888b/)

**[⬆ back to top](#linux指令)**
