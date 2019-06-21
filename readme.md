# 玩转Git三剑客笔记
## git安装
* [Git 官方文档地址](https://git-scm.com/book/zh/v2)
* [macOS 平台 Git 下载地址](https://git-scm.com/download/mac)
* [Windows 平台 Git 下载地址](https://git-scm.com/download/win)
* [Linux 平台 Git 下载地址](https://git-scm.com/download/linux)

## git教程
* [book教程](https://git-scm.com/book/zh/v2)
* git help --web log 跳转到git log 的帮助文档网页

## git配置user信息
```
git config [--local | --global | --system] user.name 'Your name'
git config [--local | --global | --system] user.email 'Your email'
```
>用于判断提交的代码指定到具体人


## 查看git配置
```
git config --list
git config --list --local
git config --list --global
git config --list --system
```

## 新建git仓库
```
git init file    新建git仓库
cd gitlocal      进入仓库
ls -al           可看到.git文件
git config --local usr.name 'minplocal'    在local中添加用户名
git config --local user.email 'king101125s@163.com'   在local中添加email
touch file    新建readme文件
git add file    通过该命令 让git监控到该文件 进入git暂存区
git status      查看文件状态
git commit -m'add' file   通过该命令 提交文件，让git管理file文件 -m'描述信息'
git commit -m'add'        通过该命令 提交文件，让git管理该目录下的文件 -m'描述信息'
git log         查看commit的说明
```

## git add
```
        git add files         gitcommit
工作目录------|--------->暂存区------|------->版本历史

git add -u  表示提交所有修改过的文件 u:updata  **推荐**
            注意：没有add 过的文件需要单独add到git暂存区
git add .   将文件的修改，文件的新建，添加到暂存区。
git add -A  将文件的修改，文件的删除，文件的新建，添加到暂存区。
```
>推荐使用 git add -u 方法

## git 基本命令
```
git rm file                     删除区中对应的文件
git mv readme readme.me         给文件重命名
git config core.ignorecase true 设置大小写敏感
git commit -am'add test'        -am 表示工作区的文件直接上传到版本库中
gitk                            图形化界面
cat .git/HEAD                   查看当前使用的分支
cd .git/refs/heads              查看当前有多少分支
                                    同git branch -v
```

### git log 实例
```markdown
commit 06c88cf84a0af3f397023187a15d24df203f8afc
Author: minp <king101125s@163.com>
Date:   Sat May 25 19:09:16 2019 +0800

    add logo

commit eb71b6241cbfcca0c563689cdf231b85ad00c004
Author: minp <king101125s@163.com>
Date:   Sat May 25 19:07:13 2019 +0800

    add js and updata css

commit 7aa257e53530a30794b287a7be72f13f09ed496b
Author: minp <king101125s@163.com>
Date:   Sat May 25 18:49:21 2019 +0800

    add index + images
```

## git 查看版本库
```markdown
git log                             查看完整的所有版本
git log --oneline                   oneline表示以简洁的形式查看提交版本
git log -n4                         n4代表查看最近4次提交
git log --oneline -n4               以上也可以组合使用
git log --all --graph               查看图形化的 log 地址
git log --oneline --all -n4 --graph 查看所有分支最近 4 条单行的图形化历史。
git help --web log                  跳转到git log 的帮助文档网页

```

## git branch分支
```markdown
git branch -v                               查看git上有多少分支
git checkout -b temp eb71b6241cbfcca0       从'eb71b6241cbfcca0'节点开始创建分支 temp
                                            eb71b6241cbfcca0 通过git log 获取到 入上面 ###git log 实例
git push --set-upstream origin temp(分支名)  推送本地分支到远程仓库
```

## git 删除分支
```
git branch -D branch_name
git branch -d branch_name:使用-d 在删除前Git会判断在该分支上开发的功能是否被merge的其它  分支。如果没有，不能删除。如果merge到其它分支，但之后又在其上做了开发，使用-d还是不能删除。-D会强制删除。老师能加一讲课来讲讲merge和rebase的区别吗
```

## 整理commit，修改commit的message 或合并commit
```
git commit --amend               修改最近一次的message（修改新的message）
git rebase -i 父commit   r       修改任意一个message  (修改旧的message)
git rebase -i 父commit   s       合并任意的commit
git rebase --abort               回滚，取消修改
```
>rebase通常用在还没有提交到集成分支之前

## 查看修改的文件内容 （暂存区和HEAD所含文件的差异）
```
git diff -cached                 比较暂存区和HEAD所含文件的差异
git diff                         比较工作区和暂存区所有文件的差异
git diff -- style.css            比较工作区和暂存取指定文件的差异
```
>判断暂存区和HEAD和工作区之间是否一致 也可以用该方法

## 暂存区文件恢复成和HEAD一样
```
git reset HEAD          恢复暂存区中所有文件
git reset HEAD <file>   恢复指定文件
```

## 工作区文件恢复为和暂存区一样
```
git checkout -- <file>
```


## 清除最近的commit提交
```
git reset --hard   commitHash     (头指针指定到commitHash位置)
```
>操作后，暂存区和工作区恢复到指定的位置
>>使用场景1. 删除commit提交
>>使用场景2. 比如做了git rm file 还没commit，使用reset命令可恢复所删除的内容

## 查看不同提交指定文件的差异
```
git diff temp master                    比较所有文件差异
git diff temp master -- index.html      比较指定文件差异
git diff 88f0f5a dcaa74b                用commitHash方式
git diff 88f0f5a dcaa74b -- index.html
```

## git 把工作区文件保存到某个状态（相当于timemachine功能）
```
git stash       保存到某个状态
git stash list  查看存放列表
git stash apply   获取最新的stash
git stash pop stash@{1}.  获取stash为1的文件
git stash pop   获取最新的stash
git stash pop stash@{1} 获取stash为1的文件
```
>apply 和pop的不同，使用pop会删除 该stash ，apply 会一致保存stash状态
>使用场景，在开发中零时加塞紧急任务

## 同步github操作步骤
```
git clone git@github.com:minplemon/explore-python.git
或者 git init explore-python
cd explore-python
git remote add mypython git@github.com:minplemon/explore-python.git 链接本地和远端，并取名mypython
git fetch mypthon master myproject        拉取远端节点  master myproject
git branch -av                            查看本地节点和远程节点
git checkout -b myproject mypython/myproject  同步远端节点mypython/myproject并生成本地节点myproject
```

## git push 把本地的文件上传到git仓库
```
git push
```

## git remote -v
```
git remote -v
```

## 技巧
1. 当出现不明确的提示，可以使用 git status 查看当前状态或提示
2. 修改工作区用checkout 修改暂存区用reset

## git 从远程仓库获取所有分支
>git clone只能clone远程库的master分支，无法clone所有分支，解决办法如下
```
git branch -a   列出所有分支名称如下：
    remotes/origin/dev
    remotes/origin/release
git checkout -b dev origin/dev  作用是checkout远程的dev分支，在本地起名为dev分支，并切换到本地的dev分支
git checkout dev                切换回dev分支，并开始开发
```
## *实际使用的时候注意*
```
git fetch
git merge
```

## 内容整理目的
1. 高效快速学习git为目的
2. 整理git笔记方便自己后期查询
3. 分享出来，希望能帮到需要的人
4. 文档如有疑问或者错误，请及时留言一起讨论
5. 文档安装学习进度更新

## 本内容来自：
* [极客时间](https://time.geekbang.org/)
* [玩转Git三剑客](https://time.geekbang.org/course/intro/145)
* [CSDN](https://so.csdn.net/so/search/s.do?q=git&t=blog&u=xiaochendefendoushi)* [简书](https://www.jianshu.com/search?q=git&page=1&type=note)




## 参考资料(推荐浏览)
* [代码托管](http://wiki.jikexueyuan.com/list/code/)
* [Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)
* [GitHub 使用手册 - 基础篇](http://wiki.jikexueyuan.com/project/github-basics/)
* [像 geek 一样写博客](http://wiki.jikexueyuan.com/project/github-page/)
