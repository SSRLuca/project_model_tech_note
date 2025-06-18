## 📄 docker 紀錄

## 建立docker

### 1.連線
ssh michliu@100.107.110.45

### 2.clone或是pull
git pull git的路徑

### 3.build image
docker build -t webapi.api1:v1 .

### 4.啟動 docker
1.建立HTTP:docker run -d --name webapi-authorization -p 8001:80 WebAPI.API1:v1

2.建立HTTPS:docker run -d --name webapi-authorization -p 8002:443 WebAPI.API1:v1

3.建立HTTP、HTTPS:docker run -d --name webapi-authorization -p 8001:80 -p 8002:443 webapi.authorization:v1


## 更新程式碼步驟

先進去專案資料夾，下git pull(輸入帳號和github的token)

1.docker build -t webapi.api1:v1 . (要先進去有dockerfile的資料夾裡面，位置會和dockerfile同層)
2.docker stop 容器名稱 (成功會出現容器名稱)
3.docker rm 容器名稱(成功會出現容器名稱)
4.docker run -d --name webapi.api1 -p 8001:80 -p 8002:443 webapi.api1:v1(成功會有CONTAINER ID)


##	Note
### 1.ls、dir查看現在目錄的檔案有哪些
### 2.查看 images
docker images 
### 3.list container(查看現在容器)
docker ps


##	其他
1.打開檔案: docker exec a10e5d84c8fd cat /app/appLog/log.txt
