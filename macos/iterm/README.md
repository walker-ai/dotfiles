### 终端会话阻碍 mac 合盖休眠

```bash
# 查看当前睡眠设置
pmset -g custom

# 将 ttyskeepawake 由 1 改为 0，恢复默认设置
sudo pmset -a ttyskeepawake 0  
```
