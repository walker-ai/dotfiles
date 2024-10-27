### 添加 github ssh key

```bash
ssh-keygen -t rsa -C "2398833647@qq.com"
```
### ssh 远程服务器使用本地代理

```bash
# local side, the former 7890 is remote port, the latter 7890 is local port
ssh -NfR 7890:localhost:7890 -p 22222 username@localhost

# login
ssh -p 22222 username@localhost

# remote side
export http_proxy=http://localhost:7890
export https_proxy=http://localhost:7890
```
#### 查看后台执行状况

```bash
ps aux | grep "ssh -NfR 7890:localhost:7890 orin"

pgrep -fl "ssh -NfR 7890:localhost:7890 orin"
```



