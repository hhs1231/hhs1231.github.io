---
title: git提交删除等操作
abbrlink: 47090
---

# git提交删除等操作

同步远程仓库

```shell
git pull
```

确定要提交的范围（.代表全部，有文件名仅提交单个）

```shell
git add 文件名
```

删除文件需要在写原因之前确定删除的文件，需要选择的范围是全部，添加等操作不需要此操作

```shell
git rm 文件名
```

编写此次提交的原因等信息

```shell
git commit -m "注释"
```

连接对应仓库（origin是笔记本应用盘中的位置，origin2是台式副硬盘中的位置，origin3是笔记本中非系统总盘中的位置，现在已经不需要了）

```shell
git remote add origin 地址（此仓库为https://gitee.com/hhs1231/c-learning.git）
```

提交

```shell
git push
```

