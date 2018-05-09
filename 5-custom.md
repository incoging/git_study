##### .gitignore -- ����һ�����ļ�

��Git�������ĸ�Ŀ¼�´���һ��.gitignore�ļ�����Ҫ���Ե��ļ������ȥ��Git�ͻ��Զ�������Щ�ļ���
**��windows�½���.gitignore�ļ�ʱ** ���������Դ���������½�һ��.gitignore�ļ���������ʾ����������ļ�����
�������ı��༭������桱���ߡ����Ϊ���Ϳ��԰��ļ�����Ϊ.gitignore�ˡ�

.gitignore�ļ����ݿ������£�
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

��Щʱ���������һ���ļ���Git����������Ӳ��ˣ�ԭ��������ļ���.gitignore�����ˣ�
```
$ git add test.class
The following paths are ignored by one of your .gitignore files:
test.class
Use -f if you really want to add them.
```
* ������-fǿ����ӵ�Git
```
$ git add -f test.class
```

##### git check-ignore ������
```
$ git check-ignore -v test.class
.gitignore:5:*.class    test.class
```
����ʾ���ǣ�.gitignore�ĵ�5�й�������˸��ļ�����Ϳ���֪��Ӧ���޶��ĸ������ˡ�

##### ���ñ���

1.Ϊstatus���ñ���st,�����Ϳ�����git st ����git status
```
$ git config --global alias.st status
```
> --global������ȫ�ֲ�����Ҳ������Щ��������̨���Ե�����Git�ֿ��¶����á�

2.����һ��git last��������ʾ���һ���ύ��Ϣ��
```
$ git config --global alias.last 'log -1'
```


##### �����ļ�

����Git��ʱ�򣬼���--global����Ե�ǰ�û������õģ�������ӣ���ֻ��Ե�ǰ�Ĳֿ������á�

ÿ���ֿ��Git�����ļ�������.git/config�ļ��У�
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
��������[alias]���棬Ҫɾ��������ֱ�ӰѶ�Ӧ����ɾ�����ɡ�

����ǰ�û���Git�����ļ������û���Ŀ¼�µ�һ�������ļ�.gitconfig�У�
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
���ñ���Ҳ����ֱ���޸�����ļ�������Ĵ��ˣ�����ɾ���ļ�����ͨ���������á�