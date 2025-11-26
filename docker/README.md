# docker 中使用代理

仅在终端中执行 `export http_proxy=...` 是无效的，因为Docker 是分为 客户端 (Client) 和 守护进程 (Daemon/Server) 两部分的。终端当输入 `docker build` 时，只是在发送指令。后台服务 (Daemon)： 真正干活（下载镜像、构建容器）的是后台的 dockerd 进程。这个进程通常是由 systemd 在开机时启动的。

关键在于： 在当前终端设置的 `export http_proxy=...` 环境变量，只对当前终端会话有效。后台那个已经启动了的 dockerd 守护进程根本“看不到” 当前窗口里设置的变量，它依然在使用默认的网络环境（直连）。

- step1 创建配置文件夹

```bash
sudo mkdir -p /etc/systemd/system/docker.service.d
```

- step2 创建代理配置文件

```bash
sudo vim /etc/systemd/system/docker.service.d/http-proxy.conf
```

- step3 写入以下内容（注意替换代理 IP 和端口）：

```bash
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:7890"
Environment="HTTPS_PROXY=http://127.0.0.1:7890"
Environment="NO_PROXY=localhost,127.0.0.1"
```

- step4 重载并重启 Docker

```bash
sudo systemctl daemon-reload
sudo systemctl restart docker
```

- step5 验证是否生效

```bash
sudo systemctl show --property=Environment docker
```
