---
title: 2019年8月24日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---



##### 1.LINUX学习

| chown  目标用户名  要修改的文件                              | 修改文件所有者  -R是递归                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| chgrp 目标组  要修改的文件                                   | 修改文件所在组  -R是递归                                     |
| chmod u=rwx,g=rx,o=x  文件或目录                             | 修改权限 u代表所有者    g代表所有组   o代表其他人   a代表所有人 |
| chmod a+r 文件名                                             | 所有用户添加读的权限   -R是递归文件夹下所有文件都设置权限    |
| crond                                                        | -e 编辑定时任务  -l 查询任务  -r 删除当前用户所有任务        |
| crond -e                                                     | 编辑任务                                                     |
| lsblk -f                                                     | 查看挂载情况                                                 |
| fdisk /设备的目录(dev)/硬盘名                                | 分区                                                         |
| n增加新的分区                                                |                                                              |
| p是否要增加一个主分区                                        |                                                              |
| 1一块主分区                                                  |                                                              |
| 默认回车就可以                                               |                                                              |
| w将分区写入硬盘                                              |                                                              |
| mkfs -t  格式化类型(ext4)   格式化的设备                     | 格式化                                                       |
| 创建一个目录  mkdir /home/ newdisk                           | 挂载重启会消失  可以使用自动挂载                             |
| 挂载入新建的目录中：mount 设备名(dev/sdb1)   新建的挂载文件的路径 |                                                              |
| vim /etc/fstab                                               | 自动挂载 永久挂载                                            |
| mount -a                                                     |                                                              |
| umount 挂载的路径                                            | 卸载分区                                                     |
| df -lh                                                       | 查看磁盘情况                                                 |
| ps -aux \| more                                              | 分页查看所有进程                                             |
| ps -aux \| grep 进程名                                       | 查看某个进程                                                 |
| ps -ef \| more                                               | 查看父进程编号                                               |
| kill 选项  进程号                                            | 杀死进程  加-9是强制干掉                                     |
| killall 进程名称                                             | 通过进程名称杀死进程  支持使用通配符                         |
| pstree                                                       | 树状结构显示进程                                             |
| pstree -u                                                    | 用户树结构显示进程                                           |
| servcie iptables restart                                     | 重启防火墙服务                                               |
| service iptables status                                      | 查看防火墙状态                                               |
| service iptables stop                                        | 关闭防火墙                                                   |
| ls -l /etc/init.d                                            | 查看服务                                                     |
| top -d 10                                                    | 十秒刷新一次                                                 |
| netstat                                                      | 监控网络服务状态 -an 按一定顺序排列   -p显示哪个进程在调用   |

```
																								进度:50%
```