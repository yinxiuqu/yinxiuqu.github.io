# 1.将本地emacs配置文件夹初始化为一个新的Git仓库：
```Bash
cd /home/yourdir/.emacs.d/
git init
```
yourdir更换为Linux系统下的用户主目录名
# 2.添加远程仓库（如果已有远程仓库）：
```Bash
git remote add origin <remote_repository_URL>
```
替换 <remote_repository_URL> 为要同步的远程仓库URL。
# 3.获取远程仓库的数据（初次同步时）：
```Bash
git pull origin master
```
替换 master 为要同步的分支名。
# 4.将本地更改推送到远程仓库：
```Bash
git add .
git commit -m "Your commit message"
git push origin master
```
替换 master 为要推送到的远程分支名。
后续修改后再同步，只需要重复第4步。同步其他文件夹，也可完全参考本文执行.