# Git命令
- [查看分支](#查看分支)


- git clone
- git branch -a
- git fetch
- git branch 新分支 远程分支
- git cheakout
- clear

## 查看分支
#### 查看【本地分支】
```
git branch
```
#### 查看【远程分支】
```
git branch -r
```
#### 查看【本地 + 远程】
```
git branch -a
```
#### 查看当前分支和跟踪关系
```
git branch -vv
```

## 本地分支 ≠ 远程分支 默认完全没有关系!
- 即使名字一样，也不能自动同步。
- 它们就像两个同名但不认识的“人”，你不牵线它们永远不会互相知道。
- 本地分支（local branch）
- 远程分支（remote branch）

### 如何关联本地分支和远程分支
#### 1. 从远程 checkout
```
git switch feature/ni_20251212
```
（Git 会自动创建本地分支并关联远程）

#### 2. 从远程 checkout
```
git checkout -b feature/ni_20251212 origin/feature/ni_20251212
```
```
git branch -u origin/feature/ni_20251212
```
把本地的 feature 分支和远程的关联起来

#### 3. 你本地创建后第一次 push
```
git push -u origin feature/ni_20251212
```
-u 就是“帮我绑定这两个分支，以后 push/pull 都知道去哪”。
#### 检查是否tracking成功
```
git branch -vv
```
结果
```
* feature/ni_20251212 ddcbb34 [origin/feature/ni_20251212] 项目初期化
  main                ddcbb34 [origin/main] 项目初期化

```

## 　`origin`
- GitLab 远程仓库 = 一个服务器
- `origin` = 你电脑给这个服务器起的昵称（默认都叫 origin）
- 当你执行 `git clone` 时
- Git 默认把你克隆的那个远程仓库命名为 `origin`
- 也可以改名
```
git remote rename origin gitlab
```
- 本地分支：`feature/ni_20251212`
- 远程分支：`origin/feature/ni_20251212`

## `git branch -a` 的输出
- `git branch -a` 的输出太长
- Git 会自动把结果丢给分页器（默认是 less）
- 终端进了 less 分页器模式
- 所以你看到 (END)，光标卡住不动

退出:

- `q`  最常用（quit）
- `Ctrl + C`


### Git 常用分支命名
| 分支名称              | 类型       | 作用        | 说明                                      |
| ----------------- | -------- | --------- | --------------------------------------- |
| `main` / `master` | 主分支      | 稳定、可发布代码  | 一般只有测试通过的代码才合并到这里                       |
| `dev`             | 开发分支     | 集中开发和集成   | 所有新功能先合并到 dev，测试稳定后再合并到 main            |
| `feature/xxx`     | 功能分支     | 开发新功能     | 从 dev 分出，每个功能一个分支，开发完成后合并回 dev          |
| `hotfix/xxx`      | 热修复分支    | 紧急修复      | 从 main 分出，修复完立即合并回 main 和 dev           |
| `release/xxx`     | 发布分支     | 版本发布准备    | 从 dev 分出，进行测试和 bug 修复，稳定后合并回 main 和 dev |
| `bugfix/xxx`      | Bug 修复分支 | 日常 bug 修复 | 通常从 dev 分出，修复后合并回 dev                   |

```
main ──────●────────●────────●─────────>（稳定发布）
           \        \        \
            \        \        \
             dev ──●───●───●───>（开发集成）
              \    \    \
               \    \    \
          feature/login  feature/cart  feature/profile

```
```
       main
        ●────────────●────────────●────────────> (稳定发布)
        │            │
        │            │
       hotfix/h1   hotfix/h2
        │            │
        └───────┐    └───────┐
                │            │
                dev ──●────●────●────●───────────────> (开发集成)
                 │    │              │            │
                 │    │              │            │
                 │   feature/login feature/cart feature/profile
                 │
                 release/v1.0
                 │
                 └─────────────> (合并回 main 和 dev)
```

### 核心区域概念

- 工作区（修改文件） → git add → 
- 暂存区（准备提交） → git commit → 
- 本地仓库（永久保存）→ git push → 
- 远程仓库（Github）

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

