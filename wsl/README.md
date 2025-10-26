## 用 mac 当跳板机，连接到 windows 中的 wsl 进行开发

### Step1

Windows 安装 OpenSSH Server服务，WSL 安装 openssh 服务

```bash
sudo apt install openssh-server
```

### Step2

打开 `/etc/ssh/sshd_config` 文件，并：

- 设置 SSH 服务的监听端口，例如：`Port 3333`
- 允许使用用户名和密码登录，设置：`PasswordAuthentication yes`
- 如果需要，允许远程 root 登录，设置：`PermitRootLogin yes`

重启 ssh 服务

```bash
service ssh restart
```

### Step3

设置开机自启动

在 `/etc/init.wsl` 中添加：

```bash
service ssh start
```

### Step4

在 windows 上配置端口转发和防火墙

1. 查看 wsl ip 地址

```bash
sudo apt install net-tools
ifconfig
```

2. 设置端口转发

打开 PowerShell 并运行以下命令：

```bash
netsh interface portproxy add v4tov4 listenaddress=0.0.0.0 listenport=3333 connectaddress=[wsl IP address] connectport=3333
```

查看所有端口代理规则

```bash
netsh interface portproxy show all
```

3. 配置 windows 防火墙

在 PowerShell 中运行：

```bash
netsh advfirewall firewall add rule name=WSL2 dir=in action=allow protocol=TCP localport=3333
```

### Step5

1. 测试本地连接

```bash
ssh root@localhost -p 3333
```

这应该可以通过本地连接到 wsl

2. 用其他用户/设备连接

```bash
ssh [username]@[ip] -p 3333
