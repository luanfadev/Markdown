# Git笔记

### 创建版本库

- 初始化  `git init`
- 把文件添加到版本库
  - 添加到暂存区(staged) `git add <file>`
    - 取消暂存 `git restore --staged <file>`
  - 提交到本地仓库 `git commit -m <message>`


### 查看
- 查看状态 `git status`
- 查看历史版本 `git log --pretty=oneline `
- 操作记录 `git reflog`
- 查看工作区和版本库different `git diff HEAD -- <file>`

### 版本管理
- 版本回退 `git reset --hard <commit_id>` 
  - `HEAD^`表示回退N(N个^)个版本
  - `8e1ee3797...` 具体版本号
    - 具体版本号的查询方式可以通过`git log`或者`git reflog`
- 放弃修改
  - 从暂存区回退到工作区 `git reset HEAD <file>`
  - 删除工作区的修改 `git checkout -- <file>`