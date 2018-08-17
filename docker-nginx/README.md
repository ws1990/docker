# 添加了echo模块的nginx
## 版本
目前仅支持mainline版本，当前（2018-08-17）最新版本为1.15.2。
## 使用说明
常见命令
```shell
# 生成镜像，请根据实际情况修改tag
docker build -t ws/nginx:1.15.2 .
# 启动nginx，请根据实际情况修改相关参数
docker run --name nginx -p 80:80 -v /conf/nginx/nginx.conf:/etc/nginx/nginx.conf -v /conf/nginx/conf.d/:/etc/nginx/conf.d/ -d ws/nginx:1.15.2
```
更多命令请参考docker-nginx官方说明文档：[nginxinc/docker-nginx](https://github.com/nginxinc/docker-nginx)