### 在 docker 中使用代理
```bash
# host side
docker build -it ...[other options] --net=host imagename /bin/bash
# container side
export http_proxy=http://localhost:8080
export https_proxy=http://localhost:8080
```
