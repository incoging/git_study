####两种方法：
#####使用SSH or 使用HTTPS(此方法直接跳转步骤3)
1.创建SSH Key,在用户主目录下，看看有没有.ssh目录(一般是隐藏文件，用ls -a 查看)，且子目录中是否由id_rsa和
id_rea.pub这两个文件，若有跳过这一步，若没有，执行下面命令:
```bash
ssh-keygen -t rsa -C "youremail@example.com"  # 地址替换成是github注册的邮箱地址
```
之后一直回车键就可以了。
结果可以在/home的.ssh目录中找到id_rsa(私钥，不能泄露)和id_rea.pub(公钥)。

2.登录github,打开用户头像的“setting”，找到“SSH and GPG Keys"选项，
点击"Add SSH Key",填上任意Title，在Key文本框里粘贴id_rsa.pub文件内容。

3.登录github，"New repository",写上名字，(若后面是克隆的话，勾选initialize ...with a README),
创建后可以直接克隆到本地一个仓库，或者与本地的一个文件夹，关联起来。
>3.1 克隆到本地
```bash
git clone git@github.com:username/git_study.git  # username是用户名，git_study是项目名
```
>>github会提供两个地址：
```
https://github.com/username/git_study.git  # 不利用前面建立的ssh，但是需要每次push时输入账号密码
git@github.com:username/git_study.git  # 使用前面两部建立的ssh，push时直接了当快速。
```
>3.2 与本地的一个文件关联
```bash
cd git_study  # 打开要关联的文件夹
git init 
git remote add origin git@github.com:username/git_study.git  # origin是远程库的名字
git push -u origin master  # 把当前的master分支推送到远程库，
# 第一次推送master分支时加上了-u，以后不必。
#第一次连接github时可能会由ssh的警告提示，无需管理。
```
