# Git的使用
---
# 初始化
* 初始化一个Git仓库,使用`git init`命令。
* 添加文件到Git仓库，分两步：
  + 第一步，使用命令`git add <file>`，注意，可反复多次使用，添加多个文件；
  + 第二步，使用命令`git commit -m “<description>”`，完成。

# 查看工作区
* 要随时掌握工作区的状态，使用git status命令。
* 如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

# 版本的跳转
HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令
`git reset --hard HEAD^`返回上一个版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100
使用：`git reset --hard commit_id`可在任意版本中穿梭

# 查看日志（主要用于查找commit_id）
穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

# 修改
- 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。
- 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD file`，就回到了场景1，第二步按场景1操作。

# Git分支管理
- 查看分支：`git branch`
- 创建分支：`git branch <name>`
- 切换分支：`git checkout <name>`
- 创建+切换分支：`git checkout -b <name>`
- 合并某分支到当前分支：`git merge <name>`
- 删除分支：`git branch -d <name>`

# 创建SSH Key
在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：`$ ssh-keygen -t rsa -C "youremail@example.com"`

# 远程库
- 要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`；
- 关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；
- 此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；

# 克隆
- 要克隆一个仓库，首先必须知道仓库的地址，然后使用`git clone`命令克隆。
- Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。
---
参考：(https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)[https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000]
