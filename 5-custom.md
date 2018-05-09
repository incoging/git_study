##### .gitignore -- 忽略一部分文件

在Git工作区的根目录下创建一个.gitignore文件，把要忽略的文件名填进去，Git就会自动忽略这些文件。
**在windows下建立.gitignore文件时** 如果你在资源管理器里新建一个.gitignore文件，它会提示你必须输入文件名，
但是在文本编辑器里“保存”或者“另存为”就可以把文件保存为.gitignore了。

.gitignore文件内容可以如下：
```
# Windows:
Thumbs.db
ehthumbs.db
Desktop.ini

# Python:
*.py[cod]
*.so
*.egg
*.egg-info
dist
build

# My configurations:
db.ini
deploy_key_rsa
```

有些时候，你想添加一个文件到Git，但发现添加不了，原因是这个文件被.gitignore忽略了：
```
$ git add test.class
The following paths are ignored by one of your .gitignore files:
test.class
Use -f if you really want to add them.
```
* 可以用-f强制添加到Git
```
$ git add -f test.class
```

##### git check-ignore 命令检查
```
$ git check-ignore -v test.class
.gitignore:5:*.class    test.class
```
会提示我们：.gitignore的第5行规则忽略了该文件，这就可以知道应该修订哪个规则了。

##### 配置别名

1.为status配置别名st,这样就可以用git st 代替git status
```
$ git config --global alias.st status
```
> --global参数是全局参数，也就是这些命令在这台电脑的所有Git仓库下都有用。

2.配置一个git last，让其显示最后一次提交信息：
```
$ git config --global alias.last 'log -1'
```


##### 配置文件

配置Git的时候，加上--global是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用。

每个仓库的Git配置文件都放在.git/config文件中：
```
$ cat .git/config
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    url = git@github.com:michaelliao/learngit.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[alias]
    last = log -1
```
别名就在[alias]后面，要删除别名，直接把对应的行删掉即可。

而当前用户的Git配置文件放在用户主目录下的一个隐藏文件.gitconfig中：
```
$ cat .gitconfig
[alias]
    co = checkout
    ci = commit
    br = branch
    st = status
[user]
    name = Your Name
    email = your@email.com
```
配置别名也可以直接修改这个文件，如果改错了，可以删掉文件重新通过命令配置。