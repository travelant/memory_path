

1.解决的问题
如果没有这项功能，用户可能需要一层一层退目录，再一层一层进目录。当然如果用户保存的有整条目录，复制一下，也会很方便，但谁有能保存了整个目录呢？可操作性不强。
2.本工具的介绍
这个工具主要用于简化切换目录操作，如果用户之前在控制台使用过一个目录，这个目录已经被记录下来，下一次，只需要输入目录的最后一个部分就可以，自动找到这条目录，并进入这个目录。这个工具的中文叫“麻袋”，命令名是wl，为什么不是md，因为md在linux里已经被占用了 ：（

3.举例说明

3.1 长目录的快速切换

下面例子，演示直接用一个目录，跳到trunk这个目录，这个就很方便使用。

root@IMMV2-DEV4:~/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv/bld-sh4/ncsi_failover# wl trunk
root@IMMV2-DEV4:~/workspace/trunk#


3.2 优先顺序

工具在找目录时，会先查找当前目录，如果有，就进当前目录，这种情况就相当于cd命令，如果没有查找历史情况，如果没有，还会查找历史目录里的某个字段，如果知道，就跳到该字段结尾的目录。

3.3 多目录的选择
如果碰到有多个一样结尾字段的情况，工具会把他们都列到屏幕上，用户可通过上下键选择，选中后按回车确认，进入该目录。

下面例子，找src的目录，工具会列出5行，用户通过上下箭头键来选择，通过回车确认即可。

wl src

/home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/bmc/bld-sh4/src                                        /home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/bmc/src   /home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv/bld-sh4/ncsi_failover/src  /home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv/ncsi_failover/src                                                                              /home3/wenlish/workspace/trunk/imm/sysserv/ncsi_failover/src



3.4 通配符*的灵活使用

本例子中使用*，来演示如果不记得全部字段的名字，只记得一部分，可以使用*做简单模糊查找。下面的例子中列出了ncsi开始的各种可能情况。

wl ncsi*

/home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv/bld-sh4/ncsi_failover  /home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv/bld-sh4/ncsi_failover/src     /home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv/ncsi_failover       /home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv/ncsi_failover/src   /home3/wenlish/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/ncsi                                                                                      /home3/wenlish/workspace/trunk/imm/sysserv/ncsi_failover
/home3/wenlish/workspace/trunk/imm/sysserv/ncsi_failover/src


3.5 也可以在很大程度上替代cd

a. 直接使用，或者带~，进入HOME
root@IMMV2-DEV4:~/workspace/trunk# wl
root@IMMV2-DEV4:~#
root@IMMV2-DEV4:~/workspace/trunk# wl ~
root@IMMV2-DEV4:~#
b. 进入上层目录
root@IMMV2-DEV4:~/workspace/trunk# wl ..
root@IMMV2-DEV4:~/workspace#
c. 进入特定目录
root@IMMV2-DEV4:~/workspace# wl 2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv
root@IMMV2-DEV4:~/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv#

是不是和cd功能很接近。


3.6 其他可选情况 
如果不想出现多选的情况，有一下两种可能。
a. 加l在最后，表明如果有多个选择，去最近去过的一个。
root@IMMV2-DEV4:~/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm/sysserv# wl trunk l
root@IMMV2-DEV4:~/workspace/trunk#
b. 加m在最后，表明如果有多个选择，去最多去过的一个。
root@IMMV2-DEV4:~/workspace/trunk# wl imm m
root@IMMV2-DEV4:~/workspace/2018-01-15-BUILD-39A-R1-18A-JD-Failover/imm#


