# github使用

## 1.  SSH keys配置
### 先检查公私钥是否已经存在
```
$ ls -al ~/.ssh
```

### 创建一套新公私钥
```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

>[官方文档](https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account)

## 2. github上创建个人仓库 （略）


## 3. 本地仓库同步到Github
```
git remote -v                查看远程版本库信息
git remote add githubname git@github.com:minplemon/studyPython.git   新增一个远端站点 githubname 表示设置远端站点名称
git fetch githubname master  指定拉去拉取githubname远程版本master分枝
git merge githubname/master  把githubname仓库的master合并
git merge -h                查看合并帮助信息
git merge --allow-unrelated-histories githup/master 合并githup上的master分支（两分支不是父子关系，所以合并需要添加 --allow-unrelated-histories
git push githubname         推送同步到githubname仓库
git push --all              把本地所有分支推送到远端站点
```

## 多人同时操作git仓库
1. 修改不同分支（不影响），最后由master统一处理分支，是merge还是放弃等
2. 修改相同分支不同文件，需要先fetch,拉去最新的信息，在进行merge
```
eg:
git fetch studygit
git merage studygit/future/git_commit
```
3. 修改不相同分支，相同文件
4. 在不同区域，修改相同分支，相同文件
```
git pull 一次搞定，比较稳健的操作是先branch -av 看状态 有不同步在fetch 在merge
```
5. 多人修改同一文件相同地方，出现冲突
```
相当于都push 文件上去的时候，出现文件修改冲突，处理了方法是直接对修改的文件 vi 在做一次修改
在 add + commmit
```
6. 一人修改了文件名和一个文件
```
直接 git pull 即可
```
7. 多人都修改了了同一个文件名
pull 之后 所有文件都会存在，需要一个单独处理
8. GitHub 同步实践
```
1. git merge master 本地同步 master
2. 通过github desktop 把本地 同步到 github网站
```

## 好的习惯
1. 在用git前先坐下git pull 本地和远端数据同步 pull = fetch + merge
2. 查看远端和本地数据是否有改动 git branch -av 有的话在git merge future/git_commit
3. 远端比本地早几个commit 用fetch，如本地也有更新需要在merge合并
4. 本地比远端早几个commit 用push
5. git branch -av 中的 ahead 和behind，ahead是本地仓库比远端仓库多commit，behind是本地仓库比远端仓库少commit
6. 查看本地和远端的状态，git branch -av
