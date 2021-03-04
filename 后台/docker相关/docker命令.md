- 进入容器内部
```shell script
docker exec -it containerId /bin/bash
```
- 传输文件给容器内部
docker容器给宿主机传送文件
```shell script
docker cp container_id:docker容器内的路径 本地保存文件的路径
```
宿主机向docker容器传送文件
```shell script
docker cp 本地文件的路径 container_id:docker容器内的路径
```
端口映射
docker -p 宿主机端口号:容器端口号
文件挂载
docker -v 宿主机地址：容器地址