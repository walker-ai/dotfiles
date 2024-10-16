## 制作ubuntu20.04启动盘

在macOS上制作Ubuntu 20.04的启动U盘可以通过以下步骤实现：

### 步骤 1：下载Ubuntu 20.04镜像文件
1. 前往[Ubuntu官方网站](https://ubuntu.com/download/desktop)下载Ubuntu 20.04的ISO文件。
2. 下载完成后，将ISO文件保存到易于找到的文件夹中，比如“下载”文件夹。

### 步骤 2：准备U盘
1. 插入至少8GB的U盘到Mac电脑。
2. 打开“磁盘工具”（可以通过在Spotlight搜索“磁盘工具”来找到）。
3. 在左侧找到你的U盘，选择后点击“抹掉”按钮。
4. 格式化U盘：
   - **名称**：随便填一个名字，比如“Ubuntu”
   - **格式**：选择“MS-DOS (FAT)”或“ExFAT”
   - **方案**：选择“GUID分区图”
5. 点击“抹掉”，完成后关闭“磁盘工具”。

### 步骤 3：将ISO写入U盘
1. 下载并安装[Etcher](https://etcher.balena.io/#download-etcher) 。
2. 打开Etcher，将刚下载的Ubuntu ISO文件拖到“Flash from file”。
3. 选择U盘作为目标设备。
4. 点击“Flash”，Etcher会自动处理并写入ISO镜像。
5. 完成后，Etcher会提示你写入完成，移除U盘即可。

## 安装一些必备的工具

可在 iso 镜像中的 `ubuntu20.04/pool/main` 中找到
