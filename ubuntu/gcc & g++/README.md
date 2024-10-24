# 安装 gcc

```bash
sudo apt-get install build-essential
```

# 不同版本切换

安装不同版本的 gcc 或 g++

```bash
sudo apt-get install gcc-9 gcc-10 g++-9 g++-10
```

```bash
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 44 --slave /usr/bin/g++ g++ /usr/bin/g++-9
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 45 --slave /usr/bin/g++ g++ /usr/bin/g++-10
```

其中 `--slave` 后面加入g++是当切换gcc版本时也同时切换g++。

```bash
sudo update-alternatives --config gcc
```

```bash
There are 3 choices for the alternative gcc (providing /usr/bin/gcc).
 
  Selection    Path              Priority   Status
------------------------------------------------------------
  0            /usr/bin/gcc       44        auto mode
 *1            /usr/bin/g++       45       manual mode
 
Press <enter> to keep the current choice[*], or type selection number:
```
