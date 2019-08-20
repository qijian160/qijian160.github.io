---
title: GIT命令表
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
| 序号 | 命令                                                 | 说明                                                         |
| ---- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 1    | $ git config --global merge.tool vimdiff             | 在初次配置git时候要县配置一个差异分析工具如：vimdiff         |
| 2    | $git init                                            | 初始化git库                                                  |
| 3    | $ git clone git                                      | 科隆git库                                                    |
| 4    | git config –global core.editor emacs                 | 设置默认使用的文本编译器                                     |
| 5    | $ git config --global merge.tool vimdiff             | 差异分析工具                                                 |
| 6    | git config ---list                                   | 查看git的配置信息                                            |
| 7    | $ git help config                                    | 查看git中的各种工具怎么使用                                  |
| 8    | git config –list                                     | 检查已有的配置信息                                           |
| 9    | git add 文件名                                       | 添加追踪文件，如果不写文件名就是该目录下的所有文件添加跟踪   |
| 10   | $ git commit -m 'initial project version'            | 提交到暂存区                                                 |
| 11   | git commit -a -m‘一段文字’                           | 跳过暂存 省略 git add –all环节                               |
| 12   | git clone https://github.com/用户名/用户名.github.io | 科隆GITHUB上的数据库到本地                                   |
| 13   | git status                                           | 检查当前文件状态                                             |
| 14   | git log                                              | 进入到库以后查看谁在什么时间修改了文件                       |
| 15   | git diff                                             | 查看为暂存和暂存区的差别                                     |
| 16   | git diff –cached                                     | 查看上次提交和未暂存区的差别                                 |
| 17   | git rm 删除的文件                                    | 删除文件                                                     |
| 18   | git rm --cached 文件                                 | 将文件在暂存区删除也就是取消跟踪                             |
| 19   | git mv 原路径+文件名     新路径+文件名               | 修改文件位置   也可以改名                                    |
| 20   | git log                                              | 检查提交记录                                                 |
| 21   | git log –oneline                                     | 显示在一行                                                   |
| 22   | git reflog                                           | 显示回退到某个修改需要退几步                                 |
| 23   | $ git commit –amend                                  | 修改最后提交 也可以说是撤销最后一次提交                      |
| 24   | git checkout 文件名                                  | 抛弃修改命令，保证回到之前的版本                             |
| 25   | git remote                                           | 可以查看当时配置的有哪些远程库，加上-v显示对应的科隆地址     |
| 26   | $ git fetch origin                                   | 从远程仓库抓取数据 正如之前所看到的，可以用下面的命令从远程仓库抓取数据到本地： |
| 27   | git remote show 远程库名                             | 查看远程库配置信息                                           |
| 28   | git remote add 别名  远程库地质                      | 给远程库添加别名                                             |
| 29   | git remote rename 老名字 新名字                      | 修改远程库名字                                               |
| 30   | $ git remote rm 库名                                 | 删除远程库                                                   |
| 31   | $git pull                                            | 分支取下来自动合并                                           |
| 32   | git tag -a 标签名  -m’作出说明’                      | 含注标签   -m后跟标签的说明                                  |
| 33   | $ git tag -s v1.5 -m 'my signed 1.5 tag'             | -s 签署标签                                                  |
| 34   | $ git tag 标签名-lw                                  | 轻量级标签                                                   |
| 35   | git tag -v 标签名 -lw                                | 验证签署标签                                                 |
| 36   | $ git push origin 标签名                             | 发送标签到远程服务器                                         |
| 37   | git branch 分支名字                                  | 创建分支                                                     |
| 38   | git checkout 分支名字                                | 切换分支                                                     |
| 39   | git reset –hard 回退历史的索引值                     | 改变head指针指向的位置                                       |
| 40   | git reset –hard                                      | 显示当前HEAD命令在哪个修改上                                 |
| 41   | git merge 要合并进来的分支名                         | 合并分支                                                     |
| 42   | git branch -d 分支名字                               | 删除分支                                                     |
| 43   | git branch                                           | 查看所有分支信息                                             |
| 44   | git branch -v                                        | 查看各个分支最后一个提交的对象                               |
| 45   | git branch --merge                                   | 查看哪些分支已被并入当前分支                                 |
| 46   | git branch –no-merged                                | 查看尚未合并的工作                                           |
| 47   | git push (远程仓库名) (分支名)                       | 推送分支到远程仓库                                           |
| 48   | $ git checkout -b sf origin/serverfix                | 跟踪远程分支                                                 |
| 49   | $ git rebase master                                  | 衍合操作                                                     |
| 50   | git rebase --onto 合并的分支 分支1  分支2            | 衍合操作改变基底分支，将分支1和分支2都为共同祖先的直接分支   |