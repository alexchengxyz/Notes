# Docker 常用指令

## 目錄

- [Docker 常用指令](#docker-常用指令)
  - [目錄](#目錄)
  - [images](#images)
  - [containers](#containers)
  - [Port forwarding](#port-forwarding)
    - [建立容器並執行指令](#建立容器並執行指令)
  - [使用容器執行程式碼](#使用容器執行程式碼)
  - [進入容器](#進入容器)
  - [Link](#link)
  - [mysql](#mysql)

## images

- 下載映像檔

```bash
docker pull
```

- 查看目前有哪些

```bash
docker images
```

- 刪除映像檔

```bash
docker rmi
```

- 強制刪除映像檔

```bash
docker rmi -f
```

- 刪除全部映像檔

```bash
docker rmi $(docker images -q)
```

## containers

- 建立容器並執行指令

```bash
docker run
```

- 操作容器(開始/停止/重新啟動)

```bash
docker start/stop/restart
```

看目前有啟動哪些容器

```bash
docker ps
```

- 看所有容器，包含關閉的

```bash
docker ps -a
```

- 停止所有容器

```bash
docker container stop $(docker container ls -aq)
```

- 刪除所有容器

```bash
docker container rm $(docker container ls -aq)
```

- 刪除容器

```bash
docker rm
```

- 查詢版本

```bash
 docker --version
```

## Port forwarding

### 建立容器並執行指令

- 執行 nginx

```bash
docker run -d --name my-nginx -p 0.0.0.0:8080:80 nginx
```

- 安裝phpmyadmin並執行容器

``` bash
docker run --name myadmin -d --link 9784673893ba:db -p 8081:80 phpmyadmin
```

- 停止容器

```bash
docker stop my-nginx
```

- 強制刪除執行中的容器

```linux
docker rm -f my-ngix
```

- 命名容器名稱

```bash
--name
```

- 設定連接port，格式 [hostIP]:[hostPorst]:[ContainerPort]

```bash
-p
```

## 使用容器執行程式碼

```bash
docker run --rm -it php
```

- 輸入要執行的程式碼，如下

```bash
docker run --rm -it php php -v
```

- 執行完指令就把容器刪除

```bash
--rm
```

- 開啟互動和終端機輸出，執行過程中有輸入就需要這兩個選項

```bash
-it
```

- 映像檔，沒有tag的話預設會用latest最新版本

```bash
php
```

- 要在容器執行的命令

```bash
php -v
```

## 進入容器

- 啟動容器並背景作業

```bash
1. docker run -d -it docker.io/nginx
```

- 進入容器

```bash
2. docker exec -it 965a /bin/bash
```

- 跳出容器

```bash
3. ctrl+p 和 ctrl+q
```

## Link

```bash
docker exec -it my-nginx2 bash
```

```bash
docker run -d --name cache -d memcached
```

```bash
docker run -d --name my-nginx --link cache:c nginx
```

```bash
docker exec -it my-nginx bash
```

```bash
#apt-get install telnet
```

```bash
#telnet c 11211
```

- 連接到某個容器，格式[容器名]:[別名]

```bash
--link
```

## mysql

> docker run -d --name mysql8 -p 8083:3306 -e MYSQL_ROOT_PASSWORD=qwer1234 mysql:8 --default-authentication-plugin=mysql_native_password

## mongoDB
```bash
> docker exec -it 容器名稱 bash
```

```bash
> mongo
```

```bash
> exit
```