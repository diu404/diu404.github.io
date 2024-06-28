[![](../images/banner.png "首页")](https://diu404.github.io)

#### linux docker内部无权限
今天安装其他软件需要授权不小心把docker容器内部对应的目录权限修改了导致docker容器内部执行报错无权限运行

查看日志
```
# docker logs -ft 容器名
Linux-x86_64 Error: 13: Permission denied
```
解决:
以root用户登录进去容器
```
# docker exec -it -u root 容器名 /bin/bash
# 修改权限命令
```
重启docker解决