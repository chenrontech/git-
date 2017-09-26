# git

分布式代码管理容器

Workspace：工作区

Stage：暂存区

Repository：仓库区（或本地仓库）

Remote：远程仓库

---

## git 常用命令

```git
// 在当前目录新建一个git仓库
git init

// 显示所有变更信息
git status

// 将指定分支合并到当前分支
git merge <branch>

//打开git仓库图形界面
gitk
```

---

## git clone

```clone
// 将远程 git 仓库克隆到本地
git clone <url>

// 将远程 git 仓库克隆到本地
git clone -b <branch> <url>
```

---

## git config

```git
// 显示当前的 git 配置
git config --list

// 编辑 git 配置文件
git config -e --global

// 设置当前项目提交代码的用户名
git config user.name <name>

// 设置当前项目提交代码的邮箱
git config user.email <email>

// 设置全局提交代码的用户名
git config --global user.name <name>

// 设置全局提交代码时的邮箱
git config --global user.email <email>

// 配置 git 图形界面编码为 utf-8
git config --global gui.encoding=utf-8
```

---

## git branch

```branch
// 查看本地所有分支
git branch

// 查看本地所有分支 并显示最后一次提交的哈希值
git branch -v

// 查看远程所有分支
git branch -r

// 查看本地和远程所有分支
git branch -a

// 新建一个分支，但依然停留在当前分支
git branch <branch>

// 删除分支
git branch -d <branch>

// 删除远程分支
$ git branch -d remote/branch
$ git push origin --delete <branch>
```

---

## git checkout

```checkout
// 跳到之前的分支
git checkout -

// 切换到另一个分支
git checkout <branch>

// 新建一个分支，且切换到新分支
git checkout -b <branch>

// 创建本地分支并关联远程分支
git checkout -b <local-branch> <origin/remote-branch>
```

```checkout
// 恢复暂存区的指定文件到工作区
$ git checkout <file>

// 恢复某个 commit 的指定文件到暂存区和工作区
$ git checkout <commit-id> <file>

// 恢复暂存区的所有文件到工作区
$ git checkout .

// 切换到上一个分支
$ git checkout -
```

---

## git fetch

```fetch
// 拉取指定分支的变化
git fetch <origin> <master>

// 拉取所有分支的变化
git fetch

// 拉取所有分支的变化，并且将远端不存在的分支同步移除
git fetch -p
```

---

## git add

```add
// 添加所有的修改到 Staging 区
git add .
git add --all

// 添加指定文件到 Staging 区
git add <files>

// 添加修改的目录到 Staging 区
git add <dir>

// 添加所有src目录下main开头的所有文件到Staging区
git add src/main*

// 添加每个变化前，都会要求确认
// 对于同一个文件的多处变化，可以实现分次提交
$ git add -p
```

---

## git commit

```commit
// 提交 Staging 的代码到本地仓库区
git commit -m "message"

// 提交 Staging 中在指定文件到本地仓库区
git commit file1-name file2-name -m "message"

// 使用新的一次 commit，来覆盖上一次 commit
git commit --amend -m "message"

// 提交工作区自上次 commit 之后的变化，直接到仓库区
$ git commit -a

// 提交时显示所有 diff 信息
$ git commit -v
```

---

## git pull

```pull
// 下载远程仓库的所有更新，并且 merge
git pull <romote-name> <branch-name>
```

---

## git push

```push
// 上传本地仓库到远程分支
git push <remote-name> <branch-name>

// 强行推送当前分支到远程分支
git push <remote-name> <branch-name> --force

// 推送所有分支到远程仓库
git push <remote-name> --all

// 推送所有标签
git push --tags

// 推送指定标签
git push origin <tag-name>

// 删除远程分支
git push origin :master

// 删除远程标签
git push origin --delete tag <tag-name>
```

---

## git log

```log
// 每个提交在一行内显示
git log --oneline

// 在所有提交日志中搜索包含 message 的提交
git log --all --grep='message'

// 获取某人的提交日志
git log --author="name"
```

---

## git stash

```stash
// 将修改过，未 add 到 Staging 区的文件，暂时存储起来
git stash

// 恢复之前 stash 存储的内容
git stash apply

// 保存 stash 并写 message
git stash save "stash test"

// 查看 stash 了哪些存储
git stash list

// 将 stash@{1} 存储的内容还原到工作区
git stash apply stash@{1}

// 删除 stash@{1} 存储的内容
git stash drop stash@{1}

// 删除所有缓存的 stash
git stash clear
```

---

## git remote

```remote
// 显示所有远程仓库
git remote -v

// 增加一个新的远程仓库
git remote add <remote-name> url

// 显示某个远程仓库的信息
$ git remote show <remote-name>
```

---

## git tag

```tag
// 创建带有说明的标签
git tag -a <name> -m "message"

// 新建一个 tag 在当前commit
git tag <name>

// 给指定 commit 打标签
git tag <name> <commit>

// 查看所有标签
git tag

// 推送到远程
git push origin --tags

// 删除本地 tag
git tag -d <name>

// 删除远程 tag
git push origin :refs/tags/<name>
```

---

## git reset

```reset
// 将未 commit 的文件移出 Staging 区
git reset HEAD

// 重置Staging区与上次commit的一样
git reset --hard

// 重置Commit代码和远程分支代码一样
git reset --hard origin/master

// 回退到上个commit
git reset --hard HEAD^

// 回退到前3次提交之前，以此类推，回退到n次提交之前
git reset --hard HEAD~3

// 回退到指定 commit，同时重置暂存区和工作区
git reset --hard commit-id

// 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset <file>
// 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard
// 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset <commit>

// 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep <commit>

// 新建一个commit，用来撤销指定commit
// 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert <commit>
```

---

## git diff

```diff
// 查看文件在工作区和暂存区区别
git diff file-name

// 查看暂存区和本地仓库区别
git diff --cached  file-name

// 查看文件和另一个分支的区别
git diff <branch-name> file-name

// 查看两次提交的区别
git diff commit-id commit-id
```

---

## git show

```show
// 查看指定标签的提交信息
git show <tag-name>

// 查看具体的某次改动
git show commit-id
```

---

## git rebase

```rebase
// 将指定分支合并到当前分支
git rebase <branch>

// 执行commit id 将rebase 停留在指定commit 处
git rebase -i <commit-id>
```

---

## git revert

```revert
// 撤销前一次 commit
git revert HEAD

// 撤销前前一次 commit
git revert HEAD^

// 撤销指定某次 commit
git revert <commit-id>
```

---

## git rm

```rm
// 删除工作区文件，并且将这次删除放入暂存区
$ git rm <files>

// 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached <file>
```
