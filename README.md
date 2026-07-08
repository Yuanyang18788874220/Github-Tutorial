# GitHub 首次上传代码完整操作指南

本文档整理了**本地代码首次上传至 GitHub 仓库**的完整流程，包含全局配置、仓库创建、代码推送、后续同步及异常解决方案，新手可直接照着实操。

## 一、全局配置 Git 用户信息（仅首次配置）

首次使用 Git 关联 GitHub，需要配置全局用户名和邮箱（与 GitHub 账号一致）。

### 1\. 配置用户名

```Plain Text
git config --global user.name "你的用户名"
git config --global user.name "Yuanyang18788874220"
```

### 2\. 配置绑定邮箱

```Plain Text
git config --global user.email "你的邮箱"
git config --global user.email "yan.august111@gmail.com"
```

### 3\. 查看配置是否生效

```Plain Text
git config --global --list
```

---

## 二、GitHub 网页端创建空仓库

1. 登录 GitHub 账号，点击右上角 **New repository** 新建仓库

2. 填写仓库名称、简介、公开/私有权限

3. **重点：取消勾选「Initialize this repository with a README」**

4. 无需勾选 License、\.gitignore，直接创建空仓库

> **说明**：若勾选初始化 README，远程仓库会存在初始提交，本地直接推送会报错，需要先拉取代码再推送，步骤更繁琐。
> 
> 

---

## 三、本地项目首次上传代码到远程仓库

适用于：本地已有完整项目文件夹，需要首次上传至新建的 GitHub 空仓库

### 1\. 进入本地项目根目录

方式1：终端切换路径

```Plain Text
cd ~/projects/my-project
```

方式2：直接在项目文件夹内右键打开终端/ Git Bash

### 2\. 初始化本地 Git 仓库

```Plain Text
git init
```

### 3\. 添加文件到暂存区

查看文件状态（可选）

```Plain Text
git status
```

添加项目所有文件到暂存区

```Plain Text
git add .
```

### 4\. 本地首次提交代码

```Plain Text
git commit -m "首次提交：项目初始化"
```

### 5\. 修改主分支名为 main（可选，统一主流规范）

```Plain Text
git branch -M main
```

### 6\. 关联远程 GitHub 仓库

替换为你自己的仓库地址，格式：`https://github.com/用户名/仓库名.git`

```Plain Text
git remote add origin https://github.com/你的用户名/my-project.git
```

查看远程关联是否成功

```Plain Text
git remote -v
```

### 7\. 推送本地代码到远程仓库

```Plain Text
git push -u origin main
```

执行完成后，刷新 GitHub 仓库页面，即可看到所有本地代码已成功上传。

---

## 四、后续日常开发代码同步流程

适用于：项目迭代更新、修改代码后重复提交推送

### 1\. 查看本地文件改动状态

```Plain Text
git status
```

### 2\. 添加改动到暂存区

添加所有改动文件

```Plain Text
git add .
```

仅添加指定单个文件

```Plain Text
git add path/to/yourfile.ext
```

### 3\. 提交本地修改

```Plain Text
git commit -m "本次更新：修复bug/新增功能/优化代码"
```

### 4\. 推送到远程仓库

```Plain Text
git push
```

---

## 五、多人协作/远程有更新时同步方案

当远程仓库有其他提交记录（多人协作、多设备开发），直接推送会报错，需先拉取远程代码合并。

### 方案1：保留线性提交历史（推荐）

```Plain Text
git pull --rebase origin main
```

### 方案2：自动合并提交记录

```Plain Text
git pull origin main
```

拉取完成后，再执行 `git push`推送本地改动即可。

---

## 六、特殊情况：仓库已初始化 README 报错解决

若创建仓库时**勾选了初始化 README**，远程仓库存在初始提交，首次推送会提示冲突。

解决方案：先拉取远程初始文件合并到本地，再推送代码

```Plain Text
git pull --rebase origin main
```

拉取成功后执行推送

```Plain Text
git push -u origin main
```

## 七、一些常用的Git操作
```Plain Text
git remote remove origin 删除当前的远程连接
git remote -v 查看远程连接状态
```

