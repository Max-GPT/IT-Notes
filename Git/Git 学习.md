## 第一次 Git 上传流程

### 1. 配置用户名邮箱
```
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

### 2. 初始化Git
```
git init
```

### 3. 添加文件到 暂存区
```
git add .
```
查看状态
```
git status
```
### 4. 提交（Commit）
```
git commit -m "first commit"
```
### 5. 关联远程仓库
```
git remote add origin https://github.com/Max-GPT/IT-Notes.git
```
origin就是给具体仓库起的本地别名。

检查是否成功
```
git remote -v
```
会有两个结果

这是因为 Git 记录远程仓库时，会把 “拉取地址” 和 “推送地址” 分开保存

`origin  https://github.com/Max-GPT/IT-Notes.git (fetch)` 拉取地址

`origin  https://github.com/Max-GPT/IT-Notes.git (push)` 推送地址

### 7. 推送到Github
```
git push -u origin main
```
`-u` = --set-upstream 

意思是以后这个本地分支（main）默认对应那个远程分支（origin/main）

`origin`远程仓库的名字(别名)

`main`要推送的分支名。


## 已经关联后的提交
```
git status
git add .
git commit -m "修改说明"
git push
```

