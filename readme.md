### 简介

这是为了方便大家做各个镜像仓库代理的

### 操作

如果你想要启动所有的镜像仓库直接执行 

`docker-compose up -d`

但是你想要单独代理某一个仓库就直接进入那个文件夹

`cd dockerhub`

`docker-compose up -d`

就好了

每一个镜像仓库对外的端口都是不一样的，当然你也可以使用nginx统一反向代理一下

#### 当你反代并开启HTTPS后，不用设置环境也可以直接使用，用法示例：
```
docker pull example.com/library/mysql:5.7
```
说明：`library`是一个特殊的命名空间，它代表的是官方镜像。如果是某个用户的镜像就把`library`替换为镜像的用户名。

#### 环境配置教程

此方法会重启Docker服务，当您有容器正在运行时，建议使用上面的方法
```
sudo vim /etc/docker/daemon.json
```
```
{
"registry-mirrors": [
"http://ip:5000"
]
}
```
```
sudo systemctl daemon-reload
```
```
sudo systemctl restart docker
```

查看配置`docker info`

### 注意

大家可以看下配置文件

默认168h小时之后会清理缓存，也就是你拉取的镜像缓存

喜欢的给个star哦！！！！


