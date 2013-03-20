git 学习总结
==================

1. git/git-flow 安装（opensuse）
------------------

```
sudo zypper in git-core
git clone https://github.com/nvie/gitflow.git
cd gitflow
git submodule init
git submodule update
sudo make install
```

2. git 练习
----------

入门 [try_git][]
练习 [gitreal][]
[try_git]: http://try.github.com
[gitreal]: http://gitreal.codeschool.com

3. 考试和看书总结
--------------

* push到的库必须是裸库，或者远程库，不能是本地的工作目录
* clone版本库会自动生成remote，默认为origin
* reset有三种回复方式：

> git reset --mixed 默认，回退版本，只保留源码

> git reset --soft 回退版本，只回退commit

> git reset --hard 彻底回退到某个版本，本地的源码也会变为上一个版本的内容 

* 回退版本的选择：一般使用HEAD，但是可以在git log的输出里面找到相应的commit的哈希串的前几位。偏移三种办法：

> HEAD@{2}

> HEAD^^

> HEAD~2

* 忽略某些文件，既可以在.gitignore也可以在项目的.git/info/exclude指定：

```
*.[oa]
*~
*.pyc
*.swp
settings_real.py
```

其它语法：

```
# 此为注释 – 将被 Git 忽略
*.a # 忽略所有 .a 结尾的文件
!lib.a # 但 lib.a 除外
/TODO # 仅仅忽略项目根目录下的 TODO 文件,不包括 subdir/TODO
build/ # 忽略 build/ 目录下的所有文件
doc/*.txt # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```

* commit直接跳过缓存区  加 -a 但是这样不安全
* 删除远程分支，2种方法：

> git push origin --delete branchName #1.7版本之后

> git push origin :branchName #其实就是推送分支

* 取消对文件的修改：git checkout -- file
* 命令别名，几个例子,当然使用oh-my-zsh的git插件已经设计了很多命令简写

> git config --global alias.co checkout

> git config --global alias.br branch

> git config --global alias.ci commit

> git config --global alias.st status

比如第一条 执行时候只需要 git co  就表示 git checkout

* 使用rebase 原理是回到两个分支（你所在的分支和你想要衍合进去的分支）的共同祖先，提取你
所在分支每次提交时产生的差异（diff），把这些差异分别保存到临时文件里，然后从当前
分支转换到你需要衍合入的分支，依序施用每一个差异补丁文件。比如某项目不是我维护，
但是需要我添加功能特性，就应该尽量rebase，这个维护者不需要整合，只需要快进或者采纳我的补丁
* 不要rebase已经推送到公共库的更新
* 权限管理器Gitosis
* 推送到不同名分支 git push origin localbranch:remotebranch
* 应用补丁 git apply/am /tmp/patch-ruby-client.patch（工作中总结）
* pull 和 fetch+merge ，在实际使用中，git fetch更安全一些，表示某个branch在服务器上的最新状态
[git: fetch and merge, don't pull]: http://longair.net/blog/2009/04/16/git-fetch-and-merge



