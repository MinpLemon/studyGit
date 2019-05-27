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