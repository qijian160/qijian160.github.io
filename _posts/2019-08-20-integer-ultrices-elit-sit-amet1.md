---
title: GIT命令表
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
| 1    | $git init                                            | 初始化git库                                                  |
| ---- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 2    | $ git clone git                                      | 科隆git库                                                    |
| 3    | git config ---list                                   | 查看git的配置信息                                            |
| 4    | git add 文件名                                       | 添加追踪文件，如果不写文件名就是该目录下的所有文件添加跟踪   |
| 5    | $ git commit -m 'initial project version'            | 提交到暂存区                                                 |
| 6    | git clone https://github.com/用户名/用户名.github.io | 科隆GITHUB上的数据库到本地                                   |
| 7    | git status                                           | 检查当前文件状态                                             |
| 8    | git diff                                             | 查看为暂存和暂存区的差别                                     |
| 9    | git diff –cached                                     | 查看上次提交和未暂存区的差别                                 |
| 10   | git rm 删除的文件                                    | 删除文件                                                     |
| 11   | git rm --cached 文件                                 | 将文件在暂存区删除也就是取消跟踪                             |
| 12   | git mv 原路径+文件名     新路径+文件名               | 修改文件位置   也可以改名                                    |
| 13   | git log                                              | 检查提交记录                                                 |
| 14   | git log –oneline                                     | 显示在一行                                                   |
| 15   | git reflog                                           | 显示回退到某个修改需要退几步                                 |
| 16   | $ git commit –amend                                  | 修改最后提交 也可以说是撤销最后一次提交                      |
| 17   | git checkout 文件名                                  | 抛弃修改命令，保证回到之前的版本                             |
| 18   | git remote                                           | 可以查看当时配置的有哪些远程库，加上-v显示对应的科隆地址     |
| 19   | $ git fetch origin                                   | 从远程仓库抓取数据 正如之前所看到的，可以用下面的命令从远程仓库抓取数据到本地： |
| 20   | git remote show 远程库名                             | 查看远程库配置信息                                           |
| 21   | git remote add 别名  远程库地质                      | 给远程地址添加别名                                           |
| 22   | git remote rename 老名字 新名字                      | 修改远程库名字                                               |
| 23   | $ git remote rm 库名                                 | 删除远程库                                                   |
| 24   | $git pull                                            | 分支取下来自动合并                                           |
| 25   | git tag -a 标签名  -m’作出说明’                      | 含注标签   -m后跟标签的说明                                  |
| 26   | $ git tag -s v1.5 -m 'my signed 1.5 tag'             | -s 签署标签                                                  |
| 27   | $ git tag 标签名-lw                                  | 轻量级标签                                                   |
| 28   | $ git push origin 标签名                             | 发送标签到远程服务器                                         |
| 29   | git branch 分支名字                                  | 创建分支                                                     |
| 30   | git checkout 分支名字                                | 切换分支                                                     |
| 31   | git reset –hard 回退历史的索引值                     | 改变head指针指向的位置                                       |
| 32   | git reset –hard                                      | 显示当前HEAD指针在哪个修改上                                 |
| 33   | $ git reset HEAD  文件名                             | 取消缓存                                                     |
| 34   | git merge 要合并进来的分支名                         | 合并分支                                                     |
| 35   | git branch -d 分支名字                               | 删除分支                                                     |
| 36   | git branch                                           | 查看所有分支信息                                             |
| 37   | git branch -v                                        | 查看各个分支最后一个提交的对象                               |
| 38   | git branch --merge                                   | 查看哪些分支已被并入当前分支                                 |
| 39   | git branch –no-merged                                | 查看尚未合并的工作                                           |
| 40   | git push (远程仓库名) (分支名)                       | 推送分支到远程仓库                                           |
| 41   | git checkout --track origin/serverfix                | 跟踪远程分支                                                 |
| 42   | $ git rebase master                                  | 衍合操作                                                     |
| 43   | git rebase --onto 合并的分支 分支1  分支2            | 衍合操作改变基底分支，将分支1和分支2都为共同祖先的直接分支   |
| 44   | git checkout – 文件名                                | 取消修改                                                     |
| 45   | git remote -v                                        | 查看远程库                                                   |
| 46   | git remote show origin                               | 查看远程库信息                                               |
| 47   | git push origin 标签名                               | 分享标签                                                     |
| 48   | git push origin –tag                                 | 分享所有标签                                                 |
| 49   | git push origin 分支名                               | 推送本地分支                                                 |
| 50   | git push origin :分支名字                            | 删除远程分支                                                 |
| 51   | git diff 原分支  目标分支                            | 分支之间的区别                                               |