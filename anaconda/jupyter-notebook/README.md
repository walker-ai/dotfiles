### 本地访问远程

server端

```bash
jupyter-notebook password
>>> (enter password)

jupyter-notebook --no-browser
```

本地

```bash
ssh -NfL 8888:localhost:8888 user@ip
```

注册环境内核

```
python -m ipykernel install --user --name=my_env --display-name "Python (my_env)"
```

