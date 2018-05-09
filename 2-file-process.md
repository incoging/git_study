##### 工作区和暂存区
###### 工作区
在电脑里能看到的目录，比如现在的git_study文件夹就是一个工作区;
工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

######
Git的版本库里有一个称为stage（或者叫index）的暂存区，
还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

![avatar](data/stage.jpg)

##### 推送文件
```bash
vim readme.md
tonight studied github.  # readme文件内容
git add readme.md  # 将文件添加到暂存区
git commit -m "wrote a readme file"  # 将文件提交到仓库，其中-m string 是添加说明。
```

>git add 是把文件添加到暂存区。   
git commit 把当前暂存区的所有内容提交到当前分支。   
之后再使用git push origin master 是把当前master分支推送到远程的origin仓库中去。

除非有新文件可以添加，不然可以直接使用
```
# -am 一定意义上表示add 和commit的合并使用，但是这个不会track到新文件
git commit -am "some str"
git push
```

##### git add -A 和git add . 的区别
* git add . ：他会监控工作区的状态树，使用它会把工作时的**所有变化**提交到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。
* git add -u ：他仅监控**已经被add的文件**（即tracked file），它会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file）。（git add --update的缩写）
* git add -A ：是上面两个功能的合集（git add --all的缩写）

##### git status -- 查看当前工作区和版本库的状态
会显示：
1.哪些东西在工作区被修改了；
2.哪些东西已经提交到了暂存区，等待被commit(提交)。
3.哪些文件没有被跟踪。

##### git diff -- 查看文件修改了什么内容
```bash
git diff filename
```

##### git log -- 查看最近的提交日志
```bash
git log 
commit 3628164fb26d48395383f8f31179f24e0882e1e0  # 版本号
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Tue Aug 20 15:11:49 2013 +0800

    append GPL

commit ea34578d5496d7dd233c827ed32a8cd576c5ee85
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Tue Aug 20 14:53:12 2013 +0800

    add distributed

commit cb926e7ea50ad11b8f9e909c05226233bf755030
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Mon Aug 19 17:51:55 2013 +0800
```

>加参数1：--pretty-onleine

```bash
git log --pretty=oneline  # 加上后面参数可以简洁输出
3628164fb26d48395383f8f31179f24e0882e1e0 append GPL
ea34578d5496d7dd233c827ed32a8cd576c5ee85 add distributed
cb926e7ea50ad11b8f9e909c05226233bf755030 wrote a readme file
```

>加参数2：--graph
```bash
git log --graph  # 可以查看分支合并情况
```

##### git reset -- 回退到以前版本
```bash
git reset --hard HEAD^  # HEAD^表示上一个版本，上上一个版本是HEAD^^,
git reset --hard HEAD~2  # 数字几表示回退到上几个版本，这个等价于HEAD^^
git reset --hard 362816  # 若已经回退到上一版本，又后悔了，又想回来，那么可以根据版本号回退
# 版本号不用输入全部，只需要输入前面的几位让git得以区分就行了
```

##### git reflog -- 显示之前的每一次命令，并且会带有版本号
```bash
git reflog
ea34578 HEAD@{0}: reset: moving to HEAD^
3628164 HEAD@{1}: commit: append GPL
ea34578 HEAD@{2}: commit: add distributed
cb926e7 HEAD@{3}: commit (initial): wrote a readme file
```

##### git checkout -- filename -- 丢弃工作区修改
```bash
git checkout -- readme.txt
```
>命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态

##### git rm filename -- 删除文件
```bash
git rm test.txt
git commit -m "remove test.txt"  # 要从版本库中删除，那么记得执行git commit
```
