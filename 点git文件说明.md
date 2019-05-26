# .git 文件目录

* COMMIT_EDITMSG
* config 当前 git 的配置文件
* description （仓库的描述信息文件）
* HEAD （指向当前所在的分支），例如当前在 develop 分支，实际指向地址是 refs/heads/develop
* hooks [文件夹]
* index
* info [文件夹]
* logs [文件夹]
* objects [文件夹] （存放所有的 git 对象，对象哈希值前 2 位作为文件夹名称，后 38 位作为对象文件名, 可通过 git cat-file -p 命令，拼接文件夹名称+文件名查看）
* ORIG_HEAD
* refs [文件夹] 
      * heads （存放当前项目的所有分支）
      * tags (存放的当前项目的所有标签，又叫做里程碑)

* cat 命令， 功能：用来显示文件。 例如 cat text.md 显示 text.md 文件的内容
* ls -al 命令， 表示列出当前目录下的所有文件（包括隐藏文件）
* git cat-file -t 命令 ， 查看 git 对象的类型
* git cat-file -p 命令， 查看 git 对象的内容
* git cat-file -s 命令， 查看 git 对象的大小
* git diff commfire1 commfire2

## HEAD的使用
1. 一个节点，可以包含多个子节点（checkout 出多个分支）
2. 一个节点可以有多个父节点（多个分支合并）
3. ^是~都是父节点，区别是跟随数字时候，^2 是第二个父节点，而~2是父节点的父节点
4. ^和~可以组合使用,例如 HEAD~2^2
