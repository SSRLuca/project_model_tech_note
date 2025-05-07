## 📄 docker 紀錄

### 1.連線
ssh michliu@100.107.110.45

### 2.clone或是pull
git pull git的路徑

### 3.build image
docker build -t webapi.api1:v1 .

### 4.啟動 docker
建立HTTP:docker run -d --name webapi-authorization -p 8001:80 WebAPI.API1:v1

建立HTTPS:docker run -d --name webapi-authorization -p 8002:443 WebAPI.API1:v1

建立HTTP、HTTPS:docker run -d --name webapi-authorization -p 8001:80 -p 8002:443 webapi.authorization:v1

## 更新程式碼

### 步驟
先進去專案資料夾，下git pull(輸入帳號和github的token)
下docker stop 容器名稱 (成功會出現容器名稱)
下docker rm 容器名稱(成功會出現容器名稱)
下docker build -t webapi.api1:v1 . (要先進去有dockerfile的資料夾裡面，位置會和dockerfile同層)
下docker run -d --name webapi.api1 -p 8001:80 -p 8002:443 webapi.api1:v1(成功會有CONTAINER ID)


##	Note
### 1.ls、dir查看現在目錄的檔案有哪些
### 2.查看 images
docker images 
### 3.list container(查看現在容器)
docker ps



