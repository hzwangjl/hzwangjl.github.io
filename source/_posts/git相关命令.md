### 新建远程分支 

``` shell
git checkout -b paper //新建本地分支 
git push origin paper:paper //将本地分支推送到远程 
```

### 删除远程分支 
``` shell
git push origin --delete <branchName> 
```

### 修改远程分支名称 
``` shell
git clone xxx.git 
cd xxx 
git checkout -b <new_branch> 
git branch -m <old_branch> <new_branch> 
git push origin --delete <old_branch> 
git push origin HEAD:<new_branch> 
```

### Merge dev 分支到主分支 
``` shell
git checkout master 
git pull origin master 
git merge dev 

# --no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并 git merge --no-ff -m "merge with no-ff" <branch> 

git status 

git push origin master 

# 查看分支合并图 
git log --graph 
```

### 切换到远程分支 
``` shell
git checkout -b dev origin/dev 
```

### 强行切换到远程分支，覆盖本地内容 
``` shell
cd xxx 
git fetch --all 

git reset --hard origin/分支 

git checkout -b 分支 origin/分支 
```

### 远程分支已更新无法提交 
``` shell 
git pull origin master 
git push -u origin master 
```

### 提交release 
``` shell
git tag -a v3.0 -m "这是4.0版本" 

git push origin v3.0 
```

### 删除 
```shell 
git tag -d v1.1 //删除本地tag 

git push origin :v1.1//删除远程tag 

#也可以这样 

git push origin --delete tag V1.1 
```

``` shell 
vim ~/.gitconfig 

[user] 
email = hzwangjialei@crop.netease.com 
name = hzwangjialei 
[credential] 

helper = store 
```

### 分支对齐（master合入） 

``` shell
git fetch origin 

git merge origin/master-netease 

# 解决相关冲突 
git push 

```

### 版本回退 
``` shell
# 回退到上一个版本 
git reset --hard HEAD^ 

# 回退到指定版本（写几个数字就可以） 
git reset --hard 1094a 

# 查看命令历史命令 
git reflog 
```

### 撤销 
``` shell
# 撤销当前工作区修改 
git checkout -- <file> 

# 撤销暂存区修改（已经 git add <file>)，放回工作区 
git reset HEAD <file> 
```

### pull 远程分支失败 
``` shell 
如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。 

# 查看远程库信息 
git remote -v 
```

### 标签 
``` 
# 打标签 
git tag v1.0 

# 查看标签 
git tag 

# 对某次提交打标签 
git tag v0.9 f52c633 

# 查看标签信息 
git show <tagname> 

# 创建带有说明的标签，用-a指定标签名，-m指定说明文字 
git tag -a v0.1 -m "version 0.1 released" 1094adb 

# 删除标签 
git tag -d v0.1 

# 推送标签到远程 
git push origin <tagname> 

# 删除远程标签 
git tag -d v0.9 # 先删除本地 

git push origin :refs/tags/v0.9 # 再删除远程 
```

### git显示颜色 
``` shell
git config --global color.ui true 
```

### 忽略文件 
``` shell
# 添加忽略list 
vim .gitignore 

# 强制添加 
git add -f <file> 

# 查看.gitignore写的是否有问题 
git check-ignore -v <file> 
```

### git上传大文件 
``` shell
brew install git-lfs 

git lfs install 

git lfs track "*.dat" #track大的文件 

#执行后，会发现.gitattributes文件多出一行 

*.dat filter=lfs diff=lfs merge=lfs -text 

git add 大文件 

git commit -m "add big files" 

git push 

#上述方法没有，则删除大文件 

#找到大文件 

find ./ -size +100M 

git lfs track "xxx" #track大的文件 

git add xxx 

git add .gitattributes 

git commit -m "add big files" 

git push 
```

### 精简命令 
``` shell

git config --global alias.st status # git st 

git config --global alias.co checkout # git co 

git config --global alias.ci commit # git ci 

git config --global alias.br branch # git br 

git config --global alias.unstage 'reset HEAD' 

# 最后一次提交信息 

git config --global alias.last 'log -1' # git last 

git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit" 

```

### alias 
``` shell
git config --global alias.st status 
```

### git-cheatsheet.pdf 
```

```