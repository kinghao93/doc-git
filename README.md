# doc-git

#### create a new repository on the command line
场景一：远程服务器已建好空仓库，此时如何提交到这个仓库中
```
echo "# doc-git" >> README.md
git init
git add README.md
git commit -m "first commit"
# 增加一个新的远程仓库，并命名
# git remote add [shortname] [url]
git remote add origin https://github.com/wanghao00/doc-git.git
# 上传本地指定分支到远程仓库
# git push [remote] [branch]
git push -u origin master
```

#### push an existing repository from the command line
```
git remote add origin https://github.com/wanghao00/doc-git.git
git push -u origin master
```
#### git 全局配置
设定本机用户名，绑定邮箱，让远程服务器知道机器的身份
```
git config --global user.name "limengqin"
git config --global user.email "XXXXX@XX.com"
```

#### 常用命令

##### 1. 项目分支
###### 1.1 查看分支
```
# 列出项目的分支
# 本地分支列表
git branch
* master
# 远程仓库分支列表
git branch -r 
  origin/master
# 列出所有本地分支和远程分支
git branch -a
* master
  remotes/origin/master
```
#### 1.2 管理分支
```
# 创建分支
# 方法一
# 新建一个分支，但依然停留在当前分支
# git branch [branch-name]
git branch branch_1
"""
git branch
  branch_1
* master

切换本地分支
git checkout branch_1 

Switched to branch 'branch_1'
git branch
* branch_1
  master
"""

方法二:
# 新建一个分支，并切换到该分支
# git checkout -b [branch]
git checkout -b branch_2
"""
Switched to a new branch 'branch_2'

git branch 
  branch_1
* branch_2
  master
"""

---
# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一分支
git checkout -
Switched to branch 'branch_1'

---
# 删除分支

# 删除分支(本地)
# git branch -d [branch-name]
git branch -d branch_2 
Deleted branch branch_2 (was 7c13ec5).

# 删除远程分支
# git push origin --delete [branch-name]
# git branch -dr [remote/branch]

git branch -dr branch_1 
error: remote-tracking branch 'branch_1' not found.
wanghao@visint:~/Desktop/doc-git-tutorial$ git branch -dr origin/branch_1 
origin/branch_1   origin/master     
wanghao@visint:~/Desktop/doc-git-tutorial$ git branch -dr origin/branch_1 
Deleted remote-tracking branch origin/branch_1 (was 7c13ec5).
wanghao@visint:~/Desktop/doc-git-tutorial$ git branch -a
* branch_1
  master
  remotes/origin/master
```

---

##### 2.xxx
# 显示有变更的文件
```
git status
"""
On branch branch_1
nothing to commit, working directory clean
"""
```
# 显示暂存区和工作区的代码差异
git diff

# 显示暂存区和上一个commit的差异
git diff --cached [file]

# 显示工作区与当前分支最新commit之间的差异
git diff HEAD

# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"

##### 3.远程同步

# 下载远程仓库的所有变动
$ git fetch [remote]

# 显示所有远程仓库
$ git remote -v

# 显示某个远程仓库的信息
$ git remote show [remote]

# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

# 上传本地指定分支到远程仓库
$ git push [remote] [branch]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

# 推送所有分支到远程仓库
$ git push [remote] --all
#### 参考:

[GIT 常用命令](https://www.cnblogs.com/chenwolong/p/GIT.html)

[Git关于pull,commit,push的总结](https://www.cnblogs.com/wnbahmbb/p/6568179.html)

[聊下git pull --rebase](https://www.cnblogs.com/wangiqngpei557/p/6056624.html)

[Gitlab简单使用指南](https://blog.csdn.net/lemonaha/article/details/69977098)
