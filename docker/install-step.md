# 安裝Docker

## 查詢OS版本

- 如果找不到 lsb_release 指令，就需要使用以下指令安裝套件

```bash
sudo yum install -y redhat-lsb-core
```

- 查看作業系統版本

```bash
lsb_release -a
```

- 查看 Kernel 版本

```bash
uname -a
```

## CentOS7 install docker

- CentOS7 系統 CentOS-Extras 庫中已內建 Docker，可以直接安裝

```bash
1. sudo yum install docker
```

- 安裝之後啟動 Docker 服務，並讓它隨系統啟動自動載入

```bash
2. sudo service docker start
```

```bash
3. sudo chkconfig docker on
```

## install images

- 啟動docker

```bash
1. sudo service docker start
```

- 搜尋要安裝的東西

```bash
2. sudo docker search centos
```

- 下載安裝的東西

```bash
3. sudo docker pull centos
```

- 查詢是否有安裝成功

```bash
4. sudo docker images
```

## 將帳號建入 docker 群組而不用使用sudo

- 建立 docker 群組

```bash
1. sudo groupadd docker
```

- 將非 root 帳號加上 docker 群組中

```bash
2. sudo usermod -G docker -a 帳號
```

- 為了要能立刻產生作用，執行 newgrp docker

```bash
3. newgrp docker
```

- 讓這個帳號立刻改成使用 docker 這個群組

```bash
4. groups
```

- 重新啟動 docker 服務

```bash
5. sudo systemctl restart docker
```
