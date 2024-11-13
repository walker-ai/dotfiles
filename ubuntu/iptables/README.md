> 如果本地机器想通过 SSH 访问目标主机（10.42.0.105），可以通过以下步骤实现端口转发，使您能够从本地机器通过宿主机（10.203.194.229）来访问目标主机。

### 步骤 1：启用 IP 转发
在宿主机上启用 IP 转发，以允许流量从宿主机转发到目标主机：

```bash
sudo sysctl -w net.ipv4.ip_forward=1
```

为了永久启用，可以编辑 `/etc/sysctl.conf` 文件，将 `net.ipv4.ip_forward=1` 取消注释并保存，然后重新加载：

```bash
sudo sysctl -p
```

### 步骤 2：设置 iptables 端口转发

在宿主机上，配置 iptables 规则，将来自宿主机特定端口的流量转发到目标主机的 SSH 端口（通常是 22）。例如，您可以选择宿主机的端口 2222 作为转发端口：

```bash
# 将宿主机的 2222 端口流量转发到目标主机的 22 端口
sudo iptables -t nat -A PREROUTING -p tcp -d 10.203.194.229 --dport 2222 -j DNAT --to-destination 10.42.0.105:22
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

### 步骤 3：允许防火墙通过宿主机的 2222 端口

如果宿主机有防火墙（如 UFW 或 firewalld）限制，请确保允许外部通过 2222 端口访问。

对于 UFW，可以使用以下命令：

```bash
sudo ufw allow 2222/tcp
```

### 步骤 4：从本地机器通过 SSH 连接到目标主机

在本地机器上，通过宿主机的 2222 端口连接到目标主机：

```bash
ssh -p 2222 user@10.203.194.229
```

这样会将 SSH 请求发送到宿主机的 2222 端口，iptables 规则会将流量转发到目标主机的 22 端口，从而实现对目标主机的访问。
