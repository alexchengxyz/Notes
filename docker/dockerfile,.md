# Dockerfile

## 建立images流程

1. 安裝 Docker。
1. 準備好打包的目標程式。
1. 撰寫 Dockerfile。
1. 執行打包程式。
1. 實際執行成 Container。

## 映像檔堆疊

- 雖然理論上一個映像檔裡可以放多個程式與服務，但 Docker 團隊建議，一個映像檔裡面只裝一個程式，再把映像檔一層一層疊起來以提供一個完整服務。

## 執行打包程式

<https://medium.com/unorthodox-paranoid/docker-tutorial-101-c3808b899ac6>

- 去建立 Docker Image 並為這個 Image 加上 tag 名稱

```linux
1. docker build . -t 名稱
```

-列出全部 images

```linux
2. docker images
```

- 如以上pull下來有 SignatureDoesNotMatch on pulling 錯誤請用以下解決方式

<https://github.com/docker/hub-feedback/issues/1636>

```linux
sudo hwclock -s
```

## 實際執行成 Container

```linux
docker run -p 3000:3000 -it 名稱
```
