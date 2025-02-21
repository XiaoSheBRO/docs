# Git

> <https://learngitbranching.js.org/>

## 提交 `commit`

### 提交规范

- `feat` 增加新功能
- `fix` 修复问题/BUG
- `style` 代码风格相关无影响运行结果的
- `perf` 优化/性能提升
- `refactor` 重构
- `revert` 撤销修改
- `test` 测试相关
- `docs` 文档/注释
- `chore` 依赖更新/脚手架配置修改等
- `workflow` 工作流改进
- `ci` 持续集成
- `types` 类型修改

示例：`git commit -m "feat: xxx"`

## 分支

::: code-tabs
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

## `HEAD`

- 位于`.git/HEAD`
  - 存储了当前分支中的某一个提交记录的引用
- 通常可以把 HEAD 看做你的上一次提交的快照。
- 默认指向当前分支上最近一次提交记录。
  - 随着提交向前移动。
- HEAD 通常情况下是指向分支名，再指向最近一次提交记录

当 `git checkout commit1`，此时 HEAD 直接指向 commit1，称为分离的 HEAD (_Detached Head_)。

```bash
git show HEAD # 检查 Head 的状态
```

> 大多数修改提交树的 Git 命令都是从改变 HEAD 的指向开始的。

## 相对引用 `^` `~`

```bash
git checkout main^ # main 分支的上一个节点
git checkout main^^ # main 分支的上两个节点
## commit1 的上一个节点
git checkout commit1
git checkout HEAD^
```

`~` 是用来在当前提交路径上回溯的修饰符
HEAD~n 表示当前所在的提交路径上的前 n 个提交
HEAD = HEAD~0
HEAD~ = HEAD~1
HEAD~~ = HEAD~2

==注意：`HEAD^^^` 并不等价于 `HEAD^3`，而是等价与 `HEAD^1^1^1`==

### 两者关系

~ 获取第一个祖先提交，^ 可以获取第一个父提交。 其实第一个祖先提交就是第一个父提交，反之亦然。 因此，当 n 为 1 时，~ 和 ^ 其实是等价的。 譬如：HEAD~~~ 和 HEAD^^^ 是等价的。

#### 强制移动分支

`git branch -f main HEAD~3` 将 main 分支强制指向 HEAD 的第 3 级 parent 提交。

## 撤销变更

撤销变更由底层部分（暂存区的独立文件或者片段）和上层部分（变更到底是通过哪种方式被撤销的）组成。

- `git reset` 分支记录回退==到==第几个提交记录来实现撤销改动，仅在本地分支有效
  - C2 所做的变更还在，但是处于未加入暂存区状态。
- `git revert` 创建一个新的提交记录，通过删除==某个==提交的变更来回退改动，可用来推送到远程分支。

## 移动提交

`git cherry-pick commitX commitY ...` 复制所需要的分支到当前分支下

## 子模块 `submodule`

git 子模块允许你将一个 Git 仓库作为另一个 Git 仓库的子目录。 它能让你将另一个仓库克隆到自己的项目中，同时还保持提交的独立。

```bash
git submodule add http://repo-name.git repo-name # 将 repo-name 仓库作为子模块放置在 /repo-name 文件夹下
git submodule update # 更新项目内子模块到最新版本
git submodule update --remote # 更新子模块为远程项目的最新版本
git submodule update --init --recursive # 递归s初始化并下载子模块仓库

git rm --cached repo-name # 删除子模块
git clone http://main-repo.git --recursive # 克隆主仓库和子模块
```

## 设置 `config`

```bash
# 设置用户信息
git config (--global) user.name "用户名"
git config (--global) user.email "邮箱"
# 设置代理：
git config (--global) http.proxy http://127.0.0.1:1080
git config (--global) http.proxy 'socks5://127.0.0.1:1080'
git config (--global) https.proxy https://127.0.0.1:1080
git config (--global) https.proxy 'socks5://127.0.0.1:1080'
# 取消代理：
git config (--global) --unset http.proxy
git config (--global) --unset https.proxy
```

## 其他常用命令

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
- `git push --set-upstream origin 分支名` 设置远程分支并推送
