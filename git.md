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

> git push origin --delete <branchName> #1.7版本之后

> git push origin :<branchName> #其实就是推送分支

* 取消对文件的修改：git checkout -- <file>



