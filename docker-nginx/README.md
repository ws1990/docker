# 添加了echo模块的nginx
## 版本
目前仅支持mainline版本，当前（2018-08-17）最新版本为1.15.2。

## 使用说明
1. 通过Dockerfile生成镜像
```shell
# 下载release中的zip包（或者tar.gz）并解压
 curl -fSL https://github.com/ws1990/docker/releases/download/1.15.2/mainline-1.15.2.tar.gz -o mainline-1.15.2.tar.gz
tar -xvf mainline-1.15.2.tar.gz
# 生成镜像，请根据实际情况修改tag
cd mainline
docker build -t ws/nginx:1.15.2 .
# 启动nginx，请根据实际情况修改相关参数
docker run --name nginx -p 80:80 -v /conf/nginx/nginx.conf:/etc/nginx/nginx.conf -v /conf/nginx/conf.d/:/etc/nginx/conf.d/ -d ws/nginx:1.15.2
docker run --name nginx -p 80:80 -v /conf/nginx/nginx.conf:/etc/nginx/nginx.conf -v /conf/nginx/conf.d/:/etc/nginx/conf.d/ -v /conf/nginx/html/:/usr/share/nginx/html/ -d ws/nginx:1.15.2
```
2. 从阿里云下载镜像
```shell
# 下载镜像并重新tag，请根据实际情况修改tag名和版本
 docker pull registry.cn-hangzhou.aliyuncs.com/wangsong/nginx-with-echo:1.15.2
docker tag imgageId your_tag:version
# 启动nginx，请根据实际情况修改相关参数
docker run --name nginx -p 80:80 -v /conf/nginx/nginx.conf:/etc/nginx/nginx.conf -v /conf/nginx/conf.d/:/etc/nginx/conf.d/ -d ws/nginx:1.15.2
docker run --name nginx -p 80:80 -v /conf/nginx/nginx.conf:/etc/nginx/nginx.conf -v /conf/nginx/conf.d/:/etc/nginx/conf.d/ -v /conf/nginx/html/:/usr/share/nginx/html/ -d ws/nginx:1.15.2
```

## 参考
[nginxinc/docker-nginx](https://github.com/nginxinc/docker-nginx)
