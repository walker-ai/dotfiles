### 场景一

我现在有一个私人的repo，其main分支上有一些历史提交。现在我想重构我的代码。我的期望是：我想将main分支暂存在一个backup-main上，然后将main分支进行清空，接着我想要设定我的upstream来自于一个开源的repo的某个commit。我想要在main分支上保存该commit及之前的所有历史提交。然后基于这个main分支进行手动开发。

1. 备份原有 main 分支

```bash
git chekcout main

git branch main

git push origin backup-main
```

2. 将本地 main “清空”并与开源仓库的某个 commit 对齐

```bash
git remote add upstream <开源仓库的git地址>

git fetch upstream
```

3. 重置本地 main 到目标 commit

```bash
git checkout main

git reset --hard <target-commit-hash>
```

4. 设置本地 main 与开源仓库分支的 upstream（可选）

一般来说，你可以让本地的 main 跟踪开源仓库（upstream）的某个分支，便于后续拉取更新：

```bash
git branch --set-upstream-to=upstream/<开源分支> main
```

当然如果你只是单纯地想基于这个 commit 做开发，不需要持续跟踪开源库的更新，也可以不设置这个 tracking。

5. 强制推送到你自己私有仓库的 main

```bash
git push origin main --force
```
