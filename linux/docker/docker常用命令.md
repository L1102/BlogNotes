# docker常用命令集合

- 查看docker镜像

```shell
docker images
```

- 查看正在运行的容器

```shell
docker ps
# 显示所有容器
docker ps -a
```

- 过滤容器列表

```shell
# 根据状态过滤容器
docker ps --filter "status=running"
# 根据名称过滤容器
docker ps --filter "name=my_container"
# 根据镜像过滤容器
docker ps --filter "ancestor=my_image"
```





- 删除镜像（执行删除操作时，要确保没有容器正在使用这些镜像，否则删除操作可能会失败）

```shell
# 删除单个镜像
docker rmi [IMAGE_ID]
# 根据镜像的仓库名和标签来删除
docker rmi [REPOSITORY]:[TAG]
# 一次删除多个镜像
docker rmi [IMAGE_ID1] [IMAGE_ID2] [IMAGE_ID3]
# 强制删除镜像 -f => --force
docker rmi -f [IMAGE_ID]
# 删除悬挂镜像（dangling images），悬挂镜像是指没有标签的镜像，通常发生在重新构建同名镜像后
docker rmi $(docker images -f "dangling=true" -q)
# 删除所有镜像
docker rmi $(docker images -a -q)
```



















