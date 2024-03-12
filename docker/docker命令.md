Docker 小命令 -- 查看所有容器对应的内部 IP 地址

```
docker inspect -f='{{.Name}} {{.NetworkSettings.IPAddress}} {{.HostConfig.PortBindings}}' $(docker ps -aq)
```

