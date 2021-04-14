# docker-compose

## 操作流程

- 請至 server 資料夾執行以下指令，安裝 node_modules 在本地端。

```linux
cd server
```

```linux
npm i
```

- 請回到本目錄執行以下指令。

```linux
cd ..
```

- 啟動 docker 服務。

```linux
sudo service docker start
```

```linux
docker-compose up --build
```

## docker compose 參數說明

- build : 指定 Dockerfile 所在的檔案路徑。
- volume : 與本地端同步更新掛載

### 端口說明

- 公開端口但不被 Docker 外部使用，僅能 Docker 內部容器連接，範例如下。

```linux
expose:
  - 9898
```

- 將容器上的8080公開端口轉送至 Docker 主機上的80端口，範例如下

```linux
ports:
  - 8080:80 (容器端口:主機端口)
```
