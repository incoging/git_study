#### 创建/操作标签
1.git tag -- 新建标签，查看标签
```bash
git checkout dev  # 切换到需要打标签的分支
git tag v1.0  # 为该分支打上标签，默认是打在最新提交的commit上
git tag  # 查看所有标签
git log  # 查看历史提交的commit id
git tag v0.9 622889  # 给历史版本，提交id为622889的历史版本打上标签
```
> 创建带有说明的标签：
```bash
git tag -a v0.1 -m "version 0.1 released" 35268  # -a 指定标签名，-m 指定说明文字
```
2.git show -- 查看标签信息
```bash
git show v0.9  # 查看对应的标签信息
```

3.git tag -d -- 删除标签
```bash
git tag -d v0.1  # 删除标签
```
>删除远程标签：(先把本地删除，再将远程删除)
```bash
git tag -d v0.9  # 删除本地标签v0.9
git push origin :refs/tags/v0.9  # 删除远程的标签
```

4.推送标签
```bash
git push origin tagname  # 把对应的标签推送到远程
git push origin --tags  # 把尚未推送到远程的标签全部推送到远程
```
