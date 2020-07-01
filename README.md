# Git笔记

### 创建版本库

- 初始化  `git init`
- 把文件添加到版本库
  - 添加/删除状态同步到暂存区(staged) `git add/rm <file>`
    - 取消暂存 `git restore --staged <file>`
  - 提交到本地仓库 `git commit -m <message>`

### 查看
- 查看状态 `git status`
- 查看历史版本 `git log --pretty=oneline `
  - 查看分支历史 `git log --graph --pretty=oneline --abbrev-commit`
- 操作记录 `git reflog`
- 查看工作区和版本库different `git diff HEAD -- <file>`

### 版本管理
- 版本回退 `git reset --hard <commit_id>` 
  - `HEAD^`表示回退N(N个^)个版本
  - `8e1ee3797...` 具体版本号
    - 具体版本号的查询方式可以通过`git log`或者`git reflog`查询
- 放弃修改
  - 从暂存区回退到工作区 `git reset HEAD <file>`
  - 删除工作区的修改 `git checkout -- <file>`

> ##### 问题  
> 从暂存区回退到工作区和取消暂存不是一样的吗?  
>> 取消暂存 `git restore --staged <file>`  
>> 从暂存区回退到工作区 `git reset HEAD <file>`

### 远程仓库 GitHub 
- 用户主目录<kbd>.ssh</kbd> 文件夹下,复制 <kbd>id_rsa.pub</kbd>里的内容到 <kbd>GitHub下SSH and GPG keys</kbd> `new SSH key`
- 提交到/删除 远程仓库
  - `git add .`
  - `git commit -m ''`
  - `git remote add/remove orgin <respository address>`
  - `git pull` // 如有必要
  - `git push -u -f origin master` // 第一次使用<kbd>-f</kbd>强制提交
- 从远程克隆项目 `git clone <respository address>`

### 分支管理

- 创建分支 `git branch <分支名>`
- 切换分支 `git switch/checkout <分支名>`
- 查看分支 `git branch`
- 合并分支 `git merge --no-ff -m '说明' <其他分支>`
- 删除分支 `git branch -d <分支名>`

> 创建并切换分支 `git checkout -b <分支名>`
> 或者 `git switch -c <分支名>` // 推荐

> 我们注意到切换分支使用 `git checkout <分支名>`，而删除工作区的修改则是 `git checkout -- <file>`，同一个命令，有两种作用，确实有点令人迷惑。因此我们推荐使用 `switch` 来做切换分支管理

> 注意合并分支时的冲突问题


### Bug分支

 - `git stash`
 - `git stash list`
 - 恢复 `git stash apply <stash@{0}>`
 - 删除/丢弃stash `git stash drop`

> 一步到位,恢复+删除stash `git stash pop`