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
>用于判断提交的代码指定到具体人
```
git config [--local | --global | --system] user.name 'Your name'
git config [--local | --global | --system] user.email 'Your email'
```

## 查看git配置
```
git config --list
git config --list --local
git config --list --global
git config --list --system
```
    

# 新建git仓库
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
# git add
>推荐使用 git add -u 方法
```
        git add files         gitcommit
工作目录------|--------->暂存区------|------->版本历史

git add -u  表示提交所有修改过的文件 u:updata  **推荐**
            注意：没有add 过的文件需要单独add到git暂存区
git add .   将文件的修改，文件的新建，添加到暂存区。
git add -A  将文件的修改，文件的删除，文件的新建，添加到暂存区。
```
# git 基本命令
```
git rm file                     删除区中对应的文件
git reset --hard                清理暂存取的文件 git status 查看到的状态，里面是空的
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
# git 查看版本库
```markdown
git log                             查看完整的所有版本
git log --oneline                   oneline表示以简洁的形式查看提交版本
git log -n4                         n4代表查看最近4次提交
git log --oneline -n4               以上也可以组合使用
git log --all --graph               查看图形化的 log 地址
git log --oneline --all -n4 --graph 查看所有分支最近 4 条单行的图形化历史。
git help --web log                  跳转到git log 的帮助文档网页

```

# git branch分支 
```markdown
git branch -v                               查看git上有多少分支
git checkout -b temp eb71b6241cbfcca0       从'eb71b6241cbfcca0'节点开始创建分支 temp
                                                eb71b6241cbfcca0 通过git log 获取到 入上面 ###git log 实例

```

