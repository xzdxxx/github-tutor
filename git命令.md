# Git常用命令
> Git基础配置
##### 查看Git版本号
  - git -v
##### 配置用户信息(全局配置，所有仓库生效)
  - git config --global user.name "Your Name"
  - git config --global user.email "Your@email.com"
##### 查看用户配置信息
  - git config --global --list
---
> 仓库初始化与克隆
##### 本地仓库初始化
  - git init
##### 仓库克隆
  - git clone <远程仓库地址>
---
> 工作区和暂存区的操作
1. 查看文件状态
  - git status
2. 添加文件到暂存区
  - git add <文件名>
  - git add .                   //添加当前目录所有文件
3. 从暂存区移除文件
  - git rm <文件名>             //工作区和暂存区的文件都移除
  - git rm --cached <文件名>    //删除暂存区保留工作区的文件
4. 撤销工作区的修改
  - git checkout -- <文件名>    //丢弃工作区的的修改(还未add的文件)
5. 暂存区回滚
  - git reset HEAD <文件名>     //将暂存区的文件回滚到工作区，撤销git add
---
> 提交与版本管理
1. 提交到本地仓库
   - git commit -m "这里写说明" //将暂存区的文件提交到本地仓库
   - git commit -am "这里写说明" //跳过暂存区，直接提交已跟踪文件的修改(新增文件需先add)
2. 查看提交历史
   - git log                   //查看完整的提交历史
   - git log --oneline         //简略查看
3. 版本回退与撤销
   - git reset --hard <版本号>  //这里回退工作区、暂存区、本地仓库
   - git reset --soft <版本号>  //这里回退本地仓库，其他均保留
   - git reset --mixed <版本号> //这里仅保留工作区，其他均回退
   - git reset --hard HEAD~1    //回退到上一版本(~2的话就是回退到前两个，以此类推)
   - git reflog                 //查看所有操作记录(用于找回误删的版本)，找到需要的版本号之后使用 git reset --hard <版本号> 可恢复
--- 
> 分支操作
1. 查看分支
   - git branch                 //查看当前分支 *(分支名)
2. 创建与切换
   - git branch <分支名>        //分支创建
   - git switch <分支名>        //分支切换
3. 重命名与删除
   - git branch -m <旧分支名> <新分支名>  //用来重命名本地分支
   - git branch -d <分支名>     //用于删除已合并的分支
   - git branch -D <分支名>     //用于删除未合并的分支
   - git push origin --delete <分支名> //用于删除远程仓库的分支
4. 合并
   - git merge <分支名>  //在这之前先切换到主分支
5. 解决合并冲突
   - 手动修改冲突的内容，如vim <冲突文件>
   - ![冲突演示](https://github.com/xzdxxx/github-tutor/blob/main/demo.png?raw=true)
   - <<<<<<< HEAD 到 ======= 是当前分支内容，======= 到 >>>>>>> feat是源分支内容
   - 弄完之后就git add <冲突文件> 再提交 git commit -m "冲突文件"
---
> 远程仓库操作
1. 关联远程仓库
   - git remote add <远程仓库名> <远程仓库地址>
   - git remote -v           //查看远程仓库详细信息
   - git remote remove       //解除关联
2. 拉取远程数据
   - git fetch               //用来拉去新的分支并创建到本地，多人协作时优先使用
   - git pull
   - git pull <远程名> <远程分支名>:<本地分支名> //拉取远程仓库到指定本地分支
4. 推送本地数据
   - git push -u origin main    //首次推送
   - git push                   //已关联后直接推送
   - git push <远程名> <本地分支名>:<远程分支名>    //推送指定本地分支到远程仓库
---
> 差异查看
- git diff                //工作区vs暂存区
- git diff --cached       //暂存区vs本地仓库
- git diff HEAD         //工作区+暂存区vs本地仓库
- git diff HEAD~1 HEAD    //提交之间的差异(~2,~3)
- git diff <分支名> <另外一个分支名>    //分支之间的差异
---
> 其他指令
- git stash              //当有其他任务进来时，可将当前任务暂时存储起来
- git stash list         //可以查看存储起来的任务放在哪里了
- git stash pop          //恢复任务并删除stash的内容
