
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

* [环境](#环境)
	* [IDE](#ide)
	* [Misc](#misc)
		* [git | github](#git-github)
		* [git 操作](#git-操作)
			* [创建本地仓库](#创建本地仓库)
			* [提交](#提交)
			* [分支](#分支)
				* [新建分支](#新建分支)
				* [切换分支](#切换分支)
				* [合并分支](#合并分支)

<!-- /code_chunk_output -->

## 环境
### IDE
- VSCode 
    写 markdown 推荐使用 **VSCode** + **Markdown Preview Enhance 插件**

    #### 有什么好处呢？
    - <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>
输入TOC可以根据`#`的标签生成链接就像一开始的这个样子。
    - VSCode 集成了一个大体上能用的git工具。提交撤回等各种主要功能都有。

- WebStorm
    写前端当然需要这玩意啦。何况我还是JB厨，连 `ToolBox` 都装了。

而且毕竟这俩都是跨平台的……

### Misc
#### git | github
- 直接在github上创建项目, 然后在本地
`git clone https://github.com/zxj5470/BDFE.git` clone项目的地址。

参考 gitee.com 的教程。
[码云（Gitee.com）帮助文档 V1.2 - 生成并部署SSH key](http://git.mydoc.io/?t=154712)
- Windows下直接用git bash的那个命令行也是有ssh-keygen的。
    - `ssh-keygen -t rsa -C "xxxxx@xxxxx.com"`
        然后一路回车（yes）基本上就行了。如果本地已经有建议跳过该步。
    - `ssh -T git@github.com`
    - `cat ~/.ssh/id_rsa.pub`
        然后复制内容
    - 打开`settings`的界面添加`ssh`

- 所以说这些个步骤有啥用呢。git clone的时候有时候是用的ssh方式而不是https方式。最主要的其实还是在push的时候免密码，这才是关键的。
- 然后git push什么的之前只要设置过一次
    `git config --global` 邮箱/账号。这里就：
    - `git config --global user.name "zxj5470"`
    - `git config --global user.email "zxj5470@gmail.com"`
    - 有没有双引号其实也无所谓的。

#### git 操作
##### 创建本地仓库
`git init`

`git remote add origin https/ssh地址`

(比如`git remote add origin git@github.com:zxj5470/BDFE`

或者 `git remote add origin https://github.com/zxj5470/BDFE.git`)

如果是用的clone就不用管这些东西了。
- 在一个总的目录下 `git clone + 项目地址` 后面不指定目录就是当前目录下的 项目地址同名文件。
- 比如我在`E盘`的`git`文件夹下执行`git clone xxxxx` 命令就会在git文件夹下生成一个`BDFE`的文件夹。在git-bash里面的地址会是`/e/git/BDFE`

##### 提交
```bash
git add 1.1/
git commit -m "1.1"
git push
```
(主分支无所谓git push后面有没有origin master，也没有冲突也不用强制-f什么的)

- commit 按照我们的习惯其实应该是暂存，commit需要记录。
- push 才是真正的提交，把文件 **传出去**

##### 分支
一般个人项目比较少接触这个
多人项目的时候会有用到。
一般就是自己checkout出一个分支，推送的时候推送过去。用pr(pull request)到origin/master分支上。

###### 新建分支
```bash
git checkout -b newbranch
```
相当于执行
```bash
git branch newbranch
git checkout newbranch
```
###### 切换分支

切换分支到 master
```bash
git checkout master
```

###### 合并分支
```bash
git merge newbranch
```
把 `newbranch` 上的东西合并到当前分支，一般情况下我们当前是 `master`
