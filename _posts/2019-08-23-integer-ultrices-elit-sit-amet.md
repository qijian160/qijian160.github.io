---
title: 2019年8月23日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---



##### 1.LINUX学习

| useradd -d 目录 用户名                    | 指定目录创建用户                                       |
| ----------------------------------------- | ------------------------------------------------------ |
| useradd -g 组名  用户名                   | 指定组创建用户                                         |
| usermod -g 用户组  用户名                 | 修改用户组                                             |
| passwd 用户名                             | 设置用户密码                                           |
| userdel 用户名                            | 删除用户保留目录                                       |
| userdel -r 用户名                         | 删除用户并删除目录                                     |
| Id 用户名                                 | 查看用户信息                                           |
| su  –   用户名                            | 切换用户                                               |
| exit                                      | 退回到上一步目录                                       |
| whoami                                    | 查看当前是哪个用户                                     |
| groupadd  组名                            | 创建组                                                 |
| goupdel 组名                              | 删除组                                                 |
| ln -s file1 lnk1                          | 软连接  就是快捷方式                                   |
| rm -rf 软连接名                           | 删除软连接                                             |
| ln file1 lnk1                             | 物理连接                                               |
| init 运行级别                             | 切换运行级别                                           |
| man   命令名                              | 帮助信息                                               |
| mkdir -p 多级目录                         | 创建多级目录                                           |
| rmdir  目录名                             | 删除空目录                                             |
| rm -rf 目录名                             | 删除非空目录                                           |
| touch 文件名                              | 创建一个空文件                                         |
| touch 文件名  文件名                      | 一次创建多个文件                                       |
| cp 原文加 目标文件                        | 拷贝文件                                               |
| cp -r 原文件及目录  目标文件及目录        | 递归拷贝整个文件夹                                     |
| mv 旧文件名  新文件名                     | 文件重命名                                             |
| mv 旧路径文件名   新路径文件名            | 移动文件                                               |
| cat 文件名                                | 查看文件内容                                           |
| cat -n 文件名                             | 查看文件内容并显示行号                                 |
| cat -n 文件名 \| more                     | 分页查看文件                                           |
| more 文件名                               | 分页查看文件                                           |
| less 文件名                               | 查看大文件                                             |
| ls -l > 文件名                            | 将ls显示的信息覆盖写入到文件中                         |
| ls -l >> 文件                             | 将ls显示的信息追加写入到文件中                         |
| cat 文件1 > 文件2                         | 将文件1的内容覆盖写入文件2中                           |
| echo ‘内容’ > 文件                        | 将内容覆盖写入到文件中                                 |
| echo ‘内容’ >> 文件                       | 将内容追加写入到文件中                                 |
| echo 内容                                 | 将内容传入控制台                                       |
| head 文件名                               | 查看文件前10行                                         |
| head -n 5 文件名                          | 查看文件前5行                                          |
| tail 文件名                               | 查看文件后10行                                         |
| tail -n 5 文件名                          | 查看文件后5行                                          |
| tail -f 文件名                            | 实时观察文件                                           |
| history                                   | 显示历史执行的命令                                     |
| find 目录 -name 文件名                    | 按名字查找文件                                         |
| find 目录 -user 用户名                    | 按用户查看文件                                         |
| find 目录 -size +10k                      | 按大小查看文件                                         |
| find 目录 -name *.txt                     | 通配符查找                                             |
| updatedb                                  | 创建locate数据库                                       |
| locate  文件名                            | 查看文件                                               |
| grep 选项  查找内容   源文件              | 在文件中查找关键字                                     |
| cat 文件名 \| grep 内容                   | 将cat查找出来的内容利用grep进行内容查找 -n代表显示行号 |
| gzip 文件名                               | 文件压缩                                               |
| gunzip 文件名                             | 解压缩                                                 |
| zip 选项  要压缩成什么样子   要压缩的内容 | 压缩文件 -r递归压缩                                    |
| unzip 选项 解压对象                       | 解压文件 -d解压到哪去                                  |
| tar -zxvf                                 | 打包指令，能压缩也能解压                               |

​	

								进度:30%
