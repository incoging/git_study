#### 分支管理
1.git checkout -b -- 创建并切换到对应分支
```bash
git checkout -b dev  # 创建并切换到dev分支
```
等价于：
```bash
git branch dev  # 创建dev分支
git checkout dev  # 切换分支到dev,即把当前分支设置为dev
```

2.git branch --查看当前分支

3.git merge -- 指定分支合并到当前分支
```bash
git merge dev  # 当前在master分支，这句命令是把dev分支合并到master分支上。
```

>强制禁用Fast forward模式，Git会生成一个新的commit，从分支历史上就可以看出分支信息。

```bash
git merge --no--ff -m "merge with no--ff" dev  # 禁用Fast forward模式，因为要创建一个新的
# commit， 所以加上-m 参数，并把描述写进去。
```

当两个分支有完全不同的提交历史时，强行合并分支
```
git merge dev --allow-unrelated-histories
```
> 输入完后，会进入vim，这时你就只需输入你这次commit的补充信息


4.git branch -d -- 删除分支
```bash
git branch -d dev  # 删除dev分支
git branch -D dev  # 强制删除dev分支
``` 

5.git stash -- 存储当前工作状态
```bash
git stash  # 存储当前的工作装填
git stash list  # 查看存储的工作列表
git stash apply stash@{0} # 恢复之前存储的工作stash@{0}，但是此时不会删除存储的内容，需要用drop来删除
git stash drop  # 删除存储的工作状态。
git stash pop  # 恢复工作之前存储的工作状态，并删除存储
```

6.git diff -- 查看文件修改内容

7.git push -- 推送本地分支到远程库
```bash
git remote -v  # 查看远程库信息 -v是显示详细信息。
git push origin branch_name  # 推送本地的一个分支到远程库
git pull 从远程库抓取内容
git check -b branch_name origin/branch_name  # 在本地创建和远程分支对应的分支
git branch --set-upstream local_branch_name origin/branch_name  # 将本地的分支和远程的分支关联起来
```
