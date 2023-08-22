# Git

> <https://learngitbranching.js.org/>

## 提交 `commit`

### 提交规范

`git commit -m "feat: xxx"`

- feat 增加新功能
- fix 修复问题/BUG
- style 代码风格相关无影响运行结果的
- perf 优化/性能提升
- refactor 重构
- revert 撤销修改
- test 测试相关
- docs 文档/注释
- chore 依赖更新/脚手架配置修改等
- workflow 工作流改进
- ci 持续集成
- mod 不确定分类的修改
- wip 开发中
- types 类型修改

> 提交前校验见 `项目管理`（待补充）

## 分支

::: code-tabs#常用命令
@tab branch

```bash
git branch # 列出本地分支
git branch branch-name  # 创建 branch-name 新分支
git branch -d branch-name # 删除 branch-name 分支
git branch -m old-branch-name new-branch-name # 重命名分支
```

@tab checkout

```bash
git checkout branch-name # 查看(切换到) branch-name 分支
git checkout -b new-branch-name # 从当前分支创建并切换到新分支
git checkout -b new-branch-name old-branch-name # 从模板分支创建并切换到新分支
```

@tab switch

```bash
git switch branch-name # 查看(切换到) branch-name 分支
git switch -c new-branch-name # 从当前分支创建并切换到新分支
```

@tab merge

```bash
git merge branch-name # 将当前分支与 branch-name 分支合并
```

:::

## 变基 `rebase`

将一个分支的新提交复制到另一个分支的末端(最后)，用于创造更加清晰的线性提交记录。

```bash
# 将 hotfix 分支变基到 main 分支并更新 main
hotfix > git rebase main
hotfix > git switch main
main > git rebase hotfix
```

## 基本概念

### `HEAD`

位于`.git/HEAD`
存储了当前分支中的某一个提交记录的引用

- 默认指向当前分支上最近一次提交记录。
- 随着提交向前移动。
- HEAD 通常情况下是指向分支名，再指向最近一次提交记录
- 通常可以把 HEAD 看做你的上一次提交的快照。

当 `git checkout commit1`，此时 HEAD 直接指向 commit1，称为分离的 HEAD (_Detached Head_)。

```bash
git show HEAD # 检查 Head 的状态
```

> 大多数修改提交树的 Git 命令都是从改变 HEAD 的指向开始的。

## 版本控制

- `git status` 仓库状态信息
- `git add 文件名` 暂存单个文件 `.` 全部文件

- `git reset 文件名` 取消暂存
- `git reset commitID` 回退版本

  - `--hard` 不保留当前所有变更
  - `--soft` 保留为(_staged_)暂存
  - `--mixed` 保留为(_Modified_)修改

- `git log` 提交日志
- `git reflog` 所有操作记录

- `git fetch` 拉取远程分支
- `git pull` 自动 fetch + merge
- `git branch -u origin/分支名` 设置远程分支(简写)
- `git push --set-upstream origin 分支名` 设置远程分支并推送 s

## 设置

### 用户信息

```bash
git config (--global) user.name "用户名"
git config (--global) user.email "邮箱"
```

### ssh 密钥认证

### 代理

```bash
设置代理：
git config (--global) https.proxy http://127.0.0.1:1080
git config (--global) https.proxy https://127.0.0.1:1080
git config (--global) http.proxy 'socks5://127.0.0.1:1080'
git config (--global) https.proxy 'socks5://127.0.0.1:1080'
取消代理：
git config (--global) --unset http.proxy
git config (--global) --unset https.proxy
```
