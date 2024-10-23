# 安装 cmake

## 方式一
```bash
sudo apt install cmake
```
## 方式二

从 https://cmake.org/download/ 下载源码，如cmake-3.24.1.tar.gz

解压源码

```bash
tar -zxvf cmake-3.24.1.tar.gz
```

进入文件夹，用 bootstrap 检查是否安装完毕，然后执行安装

```bash
cd cmake-3.24.1
./bootstrap

make -j8
sudo make install
```

## 方式三

ppa安装

添加签名密钥 
```bash
wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | sudo apt-key add -
```
将存储库添加到源列表并进行更新
```bash
sudo apt-add-repository 'deb https://apt.kitware.com/ubuntu/ bionic main'
sudo apt-get update
```

然后用apt进行安装就是最新的版本

```bash
sudo apt install cmake
```
