## 简介

    本人运维 • 几乎所有文章都基于 macOS 、vps (CentOS_7) 



## 个人网站: www.0214.live




## 项目结构:

     ◼︎0-1993 ------- 安全技术: Wireshark、Nmap、Nessus、MSF、暗网、暴破 ... 
     ◼︎1-Net --------- 网络技术: 各种服务器搭建配置详细笔记: SSR、FRP、VPN、邮箱、DNS、企业网盘 ...
     ◼︎2-Linux ------- 基础知识: SSH、防火墙、包管理器、正则式、三剑客、文件系统 ...
     ◼︎3-Script ------ 脚本笔记: Bash、Python、 AppleScript
     ◼︎4-Web -------- 前端技术: Nginx、Bootstrap ...
     ◼︎5-Django ----- Django 基础
     ◼︎6-Database -- MySQL 主从/主主、ProxySQL读写分离、LVS高可用; Redis、MongoDB... 
     ◼︎7-Virtual ------ 虚拟化技术: Docker、VMware、ESXi、Openstack ....
     ◼︎9-DevOps ---- 运维工具: Zabbix监控、Puppet部署、ELK日志分析 ....







⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️------⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️
🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵 口语表达 🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵
⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️------⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️⬛️







🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 IT 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸


🔵 AD / NFTS 

    AD: 控制电脑用的. 控制软件的安装等等.....

    NTFS: 控制公司共享文件权限.


🔵 LDAP

    轻量级目录权限访问, 一般用来控制员工权限的.







🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 OSI 七层 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

🔸 OSI 七层

    应表会传网数物。也就是只记忆每层的第一个文字。

    7. 应用层  data                    ➜ 规定数据传输协议         ➜ HTTP、FTP、SNMP、DNS、Telnet
    6. 表示层  data ah                 ➜ 数据压缩/加密/格式化     ➜  JPEG、MPEG、ASCII
    5. 会话层  data ah ph              ➜ 建立一个连接             ➜ NetBIOS
    4. 传输层  data ah ph sh          ➜ 端口与端口的通信         ➜  TCP、UDP
    3. 网络层  data ah ph sh th        ➜ 确定对方电脑的位置       ➜ IP  
    2. 链路层  data ah ph sh th nh     ➜                          ➜ ARP、RARP
    1. 物理层  data ah ph sh th nh dt  ➜ 把数据转为01这种电流脉冲 ➜  RJ-45


    比如电脑 A 给 电脑B 发文件.  这个文件就是 data 

    电脑A 首先会从 第七层到第一层  一层一层的加头.   
    然后发送给电脑B
    电脑B 收到消息 一层层的拆头, 先拆第一层的,... 拆到最后就能获取到 文件了.

    就像快递. 发快递的会进行七次包装.  然后交给快递公司 最后收快递的拆7次包装就看到真实物品了.



🔸 TCP/IP 四层
    
    4 应用层
    3 传输层
    2 网络互连层
    1 主机到网络层



🔸 两者区别

    TCP/IP 没分的那么细而已. 其实差不多的....











🔵 DNS ✔︎

🔸 简介

    互联网其实是通过 IP 来通信的. IP不好记,所以就有了域名.
    自然也需要有个服务把 域名转换成 IP地址. 这就是DNS服务.

    说起DNS 就不得不提电脑本地的 hosts 文件

🔸 Hosts 文件

    127.0.0.1	     localhost
    192.168.169.111  VM-C7
    23.105.192.96    mail.0214.help
    127.0.0.1        www.v2ex.com
    ......
    
    hosts 文件由很多行 IP 地址 + 域名 组成的
    
🔸 hosts 文件作用

    电脑要解析任何域名. 首先肯定会去查找hosts 文件.看看有没有符合的.
    有符合的 就按照 hosts 文件为准.
    没符合的 那就去查 DNS 服务器. 

    很多破解软件都会要修改 hosts 文件.
    软件其实后台会和某个网址进行通信, 来验证软件是否正版!
    在hosts 里把这个网址的IP 改成别的无效IP.  
    软件正版验证功能自然就不能联系上真正的验证服务器了.
    再进行其他的破解. 你就可以长期使用盗版了...


🔸 DNS 层次

    根域    ➜ .                        ➜ 一个点表示一个层级 
    顶级域  ➜ .com / .us / .cn         ➜ 国家/地区 使用的  
    次级域  ➜ qq.com                   ➜ 个人/公司 使用的 ➜ 一般买的就是这个域名
    子域    ➜ www.qq.com / xx.qq.com   ➜ 二级域名. xx 这个前缀你可以任意取! 只要你不嫌累
    主机名  ➜ h1.www.qq.com            ➜ 一般服务器会取个主机名. 方便区分其他服务器.


🔸 NDS 查询流程

    1. 浏览器输入网址 按下回车
    2. 电脑首先查看本地 缓存 以及 hosts 文件
    3. 如果没有缓存 hosts 文件里也没有符合项 那就通过网络 向 DNS 服务器查询.
    4. DNS 服务器有很多级别. 反正就是从低级到高级一级一级查,
    低级能查到就查到了. 低级的查不到就问高级的. 直到查到IP为止.
    5. 查到后 本地电脑会进行缓存, 下次访问就不用再查了. 能加快网速.













🔵 CDN 

🔸 CDN 简介

    把文件缓存到全球的CDN节点,
    国外的人可以到最近的CDN 节点进行下载. 
    而不用跨国跑到中国的服务器下载, 实现网络加速.

    CDN 绝对不仅仅是缓存静态文件那么点用处.甚至可以实现负载均衡. 


🔸 CDN 种类

    网页加速、流媒体服务、文件传输加速、应用协议加速

    ⦿ 网页加速:
        缓存网站静态数据.  js / css / 图片 / 静态网页 
        用户从主站获取动态内容. 从CDN 获取静态内容. 从而加快网速

    ⦿ 流媒体服务    
        视频网站.  将视频推送到离用户最近的节点. 加快响应速度,减少主服务器压力.

    ⦿ 文件传输加速    
        CDN 下载速度非常快.

    ⦿ 应用协议加速
        比如SSL.  https 虽然安全了.但是由于要加密.响应速度会慢.
        好像可以用CDN 对SSL 进行加速



🔸 域名解析!

    首先你要知道域名解析是需要专门的域名解析服务器的! 也就是DNS服务器.

    DNS 服务器 你可以自己搭建!    当然一般都是用其他现成的免费的DNS服务器.

    DNS 服务器无数个, 
    你买了域名后, 是需要设置域名服务器的!!!
    你要指定一个域名服务器来对你的域名进行解析! 
    当然这步一般人家自动帮你完成了. 不要你手动设置. 但是你要知道这个.

    比如阿里云,有自带的域名服务器! 
    你买了阿里云的域名,会自动通过阿里的DNS服务器 对你的域名进行解析.
    如果你自己搭了个DNS服务器. 可以手动设置 用你自己的DNS服务器对你的域名进行解析.



🔸 CDN 工作原理

    DNS 域名服务器也有很多种.
    一种就是 CDN 域名服务器. 其实就是个自建的DNS服务器! 取了个名字叫CDN 域名服务器.

    比如你的网站想用阿里的CDN,
    那么首先必须把你网站的 域名解析服务器设置为阿里的域名服务器.
    这样阿里才能对你的网站进行各种CDN

    阿里会在这个 DNS服务器(CDN 域名服务器) 上进行各种设置.
    把请求引流到用户最近的缓存服务器上.



🔸 CDN 负载均衡 (Nginx)

    CDN 最重要的就是性能. 响应速度....

    所以一个 CDN 节点肯定是很多服务器组成的集群. 
    集群就需要 负载均衡 技术. 
    所有请求 首先全部到 一个负载均衡器.
    由负载均衡器 决定怎么对负载进行动态分配. 从而实现负载均衡.

    一般用 Nginx 实现负载均衡! 



🔸 CDN 动态加速

    CDN动态加速是指 在CDN的DNS解析过程中. 找出一条最优路由!从而加速用户访问.

    这个就涉及理由器知识.
    路由器能自动选出一条路线. 但是路由器选的路由不是最优的!
    就好像 我在中国访问一个服务器在中国的网站. 
    真实的网络数据可能是从用户浏览器出发,先到美国再回到中国.
    虽然也能访问这个网站. 但是网速会非常慢! 体验不好.
    这时候就可以用 CDN 加速.  能找到一条最优的路由路线,加快访问速度.







普通的路由线路 不是最优的!



















🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸


🔵 LVS 
是什么 
有什么用
有几种工作模式, 分别说说原理.




🔵 Keepalived 
是什么: 
有什么用:
高可用实现的原理.
















🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 Linux 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸


🔵 Linux 开机到登录启动过程  ✔︎
    http://oldboy.blog.51cto.com/2561410/791273


    🔸 1. BIOS 自检:  

        按下开机键后电脑必须先检测电脑硬件是否正常,BIOS就是检测这个的!
        比如你笔记本摔了一下.能开机但是进不去系统.找不到原因,这时候你就需要进BIOS看看,
        如果你的BIOS 中能看到HDD,那就说明你的硬盘硬件是没问题的!!!
        如果你的BIOS 中没有 HDD 也就是BIOS识别不了你的硬盘!那么基本上你的硬盘就是挂了!
        这时候就算你硬盘插下来拿到别的电脑上也是坏的,所以有经验的维修人员会直接告诉你硬盘挂了!
        不是人家不仔细(你也许会要求人家硬盘插到别的电脑试试的),也不是人家忽悠你,这就是自信...

        BIOS 还为计算机提供最底层的硬件控制.

        BIOS  Basic Input/Output System.  是一段程序, 存放在单独一个芯片中.



    🔸 2. MBR.GPT 引导

        MBR:  Master Boot Record  主引导记录: 
            是指一个存储设备开头的512字节! 它包含操作系统的引导器个存储设备的分区表.
        
        GPT:  GUID Partition Table 是新的分区方案, 解决了MBR的一些遗留问题.
            比如MBR 最大只能支持2T的硬盘大小; 比如MBR 最多只能分4个主分区

        BIOS 会有默认的启动设备! 一般是硬盘,重装系统时需要手动设置成光盘/USB 才行.
        BIOS 会搜寻BIOS里设置的第一个存储设备中的 MBR 中的第一个分区的引导器.
        比如你设置第一个启动设备是USB, 那么电脑开机就不会去找硬盘里面的系统,而是找U盘里面的系统.
        一个U盘是可以安装好多个系统的! (U盘完全可以看成小容量的硬盘!)
        BIOS 会找U盘中 MBR里的第一个分区的引导器,这里就可以选择你要启动U盘中的那个系统.
        选择了某个U盘中的系统后就会读取分区表,然后就能加载操作系统了! 



    🔸 3. Grub 引导菜单

        电脑开机,BIOS会读取 引导介质(硬盘/USB/光盘)上最前面的512字节,主引导记录(也就是MBR)
        MBR只能存储一个系统的引导记录, 用MBR来引导的话一个硬盘只能装一个系统.
        如果你要在一个硬盘中安装多个系统,那么你需要更加灵活的引导加载程序

        由于BIOS芯片能力有限! 只能访问极少量的数据. 而引导程序一般来说不小的!
        所以大部分的引导程序会分成两部分, 也就是系统其实是分两个阶段进行引导的.
        第一部分是主要的引导程序,安装在MBR中. 第二部分引导程序就在硬盘的别的位置的!

        BIOS会读取 MBR 中的第一个阶段的主引导程序, 主引导程序中有次引导程序在硬盘中的具体位置.

        Grub 就是引导程序的第二部分! Grub 能提供 高级的GUI 界面!  而不是冷冰冰的命令行界面.


    🔸4. 加载内核kernel 

        电脑操作其实可以分成两部分: 你能看见的(用户空间) + 你看不见的(内核空间)! 
        你能看到的: 各种GUI 图形界面, 鼠标的移动 等等...
        你看不见的: 内核操作, 其实你的任何图形操作最终都是对内核的操作.图形只是方便你操作内核而已!

        Linux 内核就是让 Linux这个操作系统运行起来的核心代码!
        就像人少胳膊少腿都是不行的, 这些核心组件一个都不能少.
        但是人少点衣服什么的 完全是没问题的! 就像系统上的 QQ等软件.


    🔸5. 启动 init 进程

        Linux下有3个特殊的进程:  idle进程(PID=0)、 init进程(PID=1)、 kthreadd(PID=2)

        idle 是系统创建的第一个进程. 唯一一个不是由Kernel 产生的进程. 完成加载系统后，演变为进程调度、交换...

        init 是idle通过Kernel创建的. 是系统中所有其他进程的祖先进程.
        init 是linux 内核启动的第一个用户级进程
        Linux 中所有的进程都是init进程创建并运行的! 
        首先Linux内核启动, 然后在用户空间启动init进程,再由init创建出其他所有系统进程.
        在系统启动完成后,init将变为守护进程,监视系统其他进程.

        kthreadd 的任务就是管理和调度其他内核进程.




    🔸6. 读取 etc/inittab 配置文件,

        当init开始运行，它通过执行一些管理任务来结束引导进程，
        这些任务都记录在 /etc/inittab 文件中
        例如检查文件系统、清理/tmp、启动各种服务以及为每个终端和虚拟控制台启动getty，

        在系统完全起来之后，init为每个用户已退出的终端重启getty（这样下一个用户就可以登录）。
        init同样也收集孤立的进程：当一个进程启动了一个子进程并且在子进程之前终止了，这个子进程立刻成为init的子进程。
        对于各种技术方面的原因来说这是很重要的，知道这些也是有好处的，因为这便于理解进程列表和进程树图。



    🔸7. 其他

        • etc/rc.d/sysinit 
        • etc/rc.d/rc  (etc/rc3.d/*)
        • mingetty














🔵 命令 


组管理命令:   groupadd、groupdel、groupmod

用户管理命令:  useradd、passwd







🔵 基本命令 

网络 + 进程 + 磁盘 





🔵 Linux 优化


禁止 root 登录. 

更改ssh 端口. 



🔸精简开机启动服务

crond 
sshd
network






🔵 只要文件夹 

















🔵 进程/线程区别





🔵 Linux 运维 网络监控是必须的,
所以没工具也要会看 网络流量方面的!






🔵 磁盘的外部结构,内部结构,以及工作原理

🔵 磁盘的磁头读写数据的原理. 什么是扇区,磁道 柱面

🔵磁盘存储数据的最小单位是 
    某业务数据为10-100M的视频文件, 如何配置单位大小

🔵 一个硬盘最多可以分多少个主分区, 为什么




🔵 inode 
    http://www.ruanyifeng.com/blog/2011/12/inode.html




🔵 软硬链接的区别 ✔︎


    在Linux系统中，链接分为两种:  硬链接（Hard link）   软链接（Symbolic Link）


    ①默认不带参数的情况下，ln创建的是硬链接，带-s参数的ln命令创建的是软链接。

    ②硬链接文件与源文件的inode节点号相同，而软链接文件的inode节点号，与源文件不同，

    ③ln命令不能对目录创建硬链接，但可以创建软链接。对目录的软链接会经常使用到。

    ④删除软链接文件，对源文件和硬链接文件无任何影响。

    ⑤删除文件的硬链接文件，对源文件及软链接文件无任何影响。

    ⑥删除链接文件的源文件，对硬链接文件无影响，会导致其软链接失效（红底白字闪烁状）。

    ⑦同时删除源文件及其硬链接文件，整个文件才会被真正的删除。

    ⑧很多硬件设备的快照功能，使用的就是类似硬链接的原理。

    ⑨软链接可以跨文件系统，硬链接不可以跨文件系统。




    首先你要知道 文件在硬盘中其实是分成好几个部分 分别存储的!
    就像字典!   字典是由前面几页的索引目录+内容组成的!
    一个文件其实是分成两部分的, inode部分(文件名+文件属性...); 文件真正内容另一部分!
    一个文件就像字典中的一个词语! 

    软链接可以看成快捷方式, 硬链接可以看成文件备份!

    删除软链接 对源文件以及硬链接无任何影响.
    删除硬链接 对源文件以及软链接无任何影响.
    删除原文件 对硬链接无影响, 但是软链接会失效.
    同时删除源文件+硬链接 才能真正删除一个文件.

    很多硬件设备的快照功能 使用的就是类似硬链接的原理!!! 
    软链接可以跨文件系统. 硬链接不能跨文件系统.

    硬链接文件与源文件的inode节点号相同. 而软链接文件的inode节点号与源文件不同.?????
    








🔵 正则式 三剑客使用..











🔵 Linux 文件删除原理 ✔︎

    Linux 通过Link数量来控制文件删除.当一个文件不存在任何链接的时候,这个文件才会被删除.

    每个文件都会有两个 link 计数器: i_count、i_nlink

    i_count 的意义是当前文件使用者(被调用)的数量. ➜  可以理解为 内存引用计数器
    i_nlink 的意义是介质链接的数量(硬链接的数量). ➜  可以理解为 磁盘引用计数器.

    当一个文件被某一个进程引用时,对应的 i_count 就会增加.
    当一个文件被创建硬链接的时候,对应的 i_nlink 就会增加.

    rm 删除命令,实际是减少磁盘引用数! 也就是 i_nlink 的值.
    如果文件没有其他的硬链接,你只要删除一次就可以把文件删除.
    但是!如果你的文件正在被调用,比如你用vi在编辑这个文件.
    这时候你是可以删除这个文件的, 但是你会发现,你打开的vi窗口没有自动关闭!
    其实当你打开(调用)某个文件的时候, 该文件的 i_count 数量会增加(不为0)!
    这时候就算你用rm 删除命令.把 i_nlink 的数量删到0. 系统并没有真正删除该文件.
    只有当 i_nlink 和 i_count 都是0的时候! 文件才会被真正删除.
    这里也就是你要退出vi后, 系统才会真正删除这个文件.

    现在我们不说调用. 只说删除.
    执行rm操作删除的文件是否可以被找回呢!?
    rm 操作只是将文件的 i_nlink 减少了, 或者说置0了, 实际就是将文件的inode的删除了!
    但是文件其实是两部分组成的 inode + 真实数据.
    rm 并没有删除文件实体(真实数据).
    如果执行rm后, 立刻停止电脑, 数据是可以被找回的. 
    如果执行rm后, 你还对磁盘进行频繁的读取,那么新的数据会很可能会覆盖掉你旧的真实数据.
    这时候文件会被真正的回收了,这时候神仙也没办法了.









🔵 Linux 0-6 运行级别的各自行义 ✔︎

    0：关机
    1：单用户模式
    2：多用户-无网络服务.   
    3：多用户-完整的多用户模式. 有网络支持（文本模式，工作中最常使用的模式）
    4：保留，未使用
    5：多用户-完整的多用户模式, 有网络支持 (X-Window 图形界面模式)
    6：重新引导系统，即重启

    运行级别: 操作系统当前正在运行的功能级别, 
    能让一些程序在某个级别启动,而在另一个级别不启动

    Linux 的登录模式有0-9共十种.
    Unix 一般只有1-6是有效的.不同的级别有不同的功能.

    /etc/rc.d/ 中放着各种脚本,每个运行级别有对应文件夹,
    你把脚本放到哪个文件夹中就会在相应级别运行该脚本
    /etc/rc.d/init.d 
    /etc/rc.d/rc0.d
    /etc/rc.d/rc1.d
    /etc/rc.d/rc2.d
    /etc/rc.d/rc3.d
    /etc/rc.d/rc4.d
    /etc/rc.d/rc5.d
    /etc/rc.d/rc6.d

    标准的Linux 运行级别是 3 或者 5
    模式3 就是多用户文本模式. 模式5就是 GUI 图形模式.

    在终端中，我们可以键入 init <运行级别> 来切换运行级别来达到某种目的，
    如输入 init 0 使系统关机，输入 init 6 使系统重启.

    默认的运行级别可以通过修改 /etc/inittab 文件来改变，
    该文件在接近开头的地方有一行与下面相似： id:5:initdefault:
    把这一行中的数字改成你想要的运行级别。所做改变在系统重新引导之后才会生效。

    不同的运行级有不同的用处，也应该根据自己的不同情形来设置。
    例如，如果丢失了root口令，那么可以让机器启动进入单用户状态来设置。
    在启动后的lilo提示符下输入： 　　init=/bin/sh rw 　　
    就可以使机器进入运行级1 ，并把root文件系统挂为读写。
    它会跳过所有系统认证，让你使用passwd程序来改变root口令，然后启动到一个新的运行级







🔵 脚本中单引号、双引号、不加引号的简单区别;✔︎

    脚本用变量的时候特别要注意 引号!

    单引号: 所见即所得,单引号里面的内容会一模一样输出, 你引号里面写的什么就输出什么!

    双引号: 双引号里面如果有变量,那么输出内容 会变成变量的内容.而不是引号里面的内容.

    无引号: 
        不会将含有空格的字符串视为一个整体输出, 
        如果内容中有命令、变量等，会先把变量、命令解析出结果，然后在输出最终内容来，
        如果字符串中带有空格等特殊字符，则不能完整的输出，需要改加双引号，一般连续的字符串，数字，路径等可以用。

    例子: 
    echo '`date`'  ➜  单引号时看到啥就显示啥  ➜  `date`
    echo "`date`"  ➜  双引号里面的变量，会先把变量解析成具体内容在显示 ➜  Sat Oct 29 18:02:59 CST 2011
    echo `date`    ➜  对于连续的字符串等内容一般不加引号也可，加双引号一般比较保险 ➜ Sat Oct 29 18:03:08 CST 2011


















🔵 Crontab 的作用.以及注意点

crontab 定时执行命令! 


















🔵 Lunux 如何实现 系统集权分治的权限分级精细管理


🔵 服务器账户日志审计的5种解决方案









🔵 什么是文件系统, 说出你知道的文件系统.

🔵 nfs 网络文件系统的工作原理.

🔵 ext2 文件系统的原理.

🔵 文件系统的种类
















🔵 什么是 rsync 有什么生产环境应用


🔵请描述ssh免密码验证的3种分发控制管理解决方案实现过程。




🔵你了解过有哪些批量部署、分发管理服务器解决方案(13种解决方案)


🔵 24.生产场景下，DELL R710服务器 6块600GSAS盘，计划装系统部署mysql从数据库提供读服务。请你描述从做RAID开始到安装系统后提供业务使用前的整个思想及操作过程。




🔵25.使用linux 命令模式或rescue(救援模式)修复/etc/fstab。



🔵26.root密码忘记了，想重新获取root密码怎么做？




🔵27.请问如何优化linux系统。






🔵 网络 








🔵 查看进程





🔵 防火墙




🔵 









🔵 邮箱 

sendmail  自建邮箱...













🔵 LNMP LAMP













🔵


28.一台LAN内主机无法上网（打不开网站），请给出你的排查步骤？
29.请描述，如何通过shell监控web及数据库服务，请给出你的思路或方法？
30.请描述下OSI7层模型及tcp/ip的3次握手。
31.mysql主从同步原理，生产情况数据库你是如何备份的？如何实现增量备份及恢复？
32.mysql常用存储引擎及原理区别。
33.请问如何优化数据库？
34.请问如何优化web服务器（apache and nginx）？
35.一台办公室内主机无法上网（打不开网站），请给出你的排查步骤？
36.作为一个运维人员，有运营人员反映我们的网站etiantian.org打开慢，这是你如何排查？
37. 请问你如何理解网站并发的概念。
38.你的公司网站并发是多少？访问量是多少？
39.描述mysql主从同步原理。
40.描述mysql主从同步部署。
41.描述mysql root密码忘了怎么办？
42.描述MyISAM与Innodb数据库引擎特点与区别？
43.描述mysql多实例部署。
44.描述如何查看mysql的命令帮助，请举例。
45.描述mysql增量备份和恢复过程。







🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 Apache 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸
常用模式:


apache + php  VS Nginx + PHP









🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 Nginx 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸


🔵 反向代理 ✔︎


    🔸 什么是反向代理

        如果服务器只有一台
        用户(浏览器) 发起 HTTP 请求 ➜ 直接到服务器! 

        如果服务器是一个集群! 
        用户(浏览器) 发起 HTTP 请求 ➜ 代理服务器 ➜  集群中的某台服务器

        两者的区别就是中间的代理服务器. 
        代理服务器. 假装是真正的服务器. 这就是反向代理.



    🔸 为什么要反向代理 (简)  ➜  为了负载均衡

        你不用反向代理. 服务器只能有一台. 处理能力有限.
        你用了反向打理. 服务器可以无上限. 处理能力也无上限



    🔸 如何反向代理.
        看下面负载均衡用法就知道了.
        location 里的设置就是反向代理设置.
        



🔵 负载均衡 ✔︎

    Nginx 作为高并发的web服务器,  企业肯定是用 web 服务器集群了.
    集群就涉及到负载的分配, 因为服务器的配置有高有低. 
    避免出现某台服务器空着, 另外的服务器却忙的要死的情况.

    假设主服务器为A (80) 从服务器为 B (8080) C(8081)  D (8082)...
    外面的所有请求都 解析到 A 服务器. 
    然后在A上面 通过修改 Nginx 配置文件来进行负载均衡. 把压力分配给 BCD...

    大概就是先把服务器添加到 upstream 参数中.  然后配置 location 

        upstream yongle.com {
            server 127.0.0.1:8881;
            server 127.0.0.1:8882;
            server 127.0.0.1:8888;
        }

        server{ 
            listen 80; 
            server_name yongle.com; 
            location / { 
                proxy_pass         http://yongle.com; 
                proxy_set_header   Host             $host; 
                proxy_set_header   X-Real-IP        $remote_addr; 
                proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for; 
            } 
        }



    🔸 负载均衡 4种配置方案. 

        就是4中分配压力的方式而已. 
        那台配置高就多分配点请求.
        那台服务器的连接数量最少就分配给哪台
        也可以每个服务器一次  轮流来分配...



🔵 SSL  ✔︎

    HTTPS证书就是在 web 服务器上设置的. 
    不管是 Apache 还是 Nginx 
    只要先获取HTTPS证书.然后修改对应的配置文件就可以启用HTTPS了






🔵 性能优化  90% 

    ⦿ 开启 Gzip , 
        压缩数据. 减少服务器网络压力,还能加快客户端访问速度.
        但是这个压缩比例不能太高. 这个是要CPU来压缩的. 


    ⦿ Buffers
        缓冲区!  设置太小. Nginx 会不断的写临时文件. 导致磁盘读写非常频繁.


    ⦿ keep-alive  Timeout 
        设置超时! 如果客户端没反应 就断开连接. 减轻服务器压力.


    ⦿ 日志
        日志用不到就关了... 频繁的日志对磁盘还是有压力的.
        就算要用日志, 也设置下日志等级. 不要什么操作都记录到日志中...


    ⦿ 静态文件缓存
        能缓存的就缓存... 快很多


    ⦿ 并发连接数 ???


    ⦿ 限制单个用户IP的连接数
        防止某些疯狂的用户. 用爬虫什么的抓你服务器的数据.

































🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 网络排错 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸
                参考  http://xpleaf.blog.51cto.com/9315560/1689438


🔵 基础知识 
    
    🔸 TCP/IP 

        OSI七层不需要非常了解. 
        但是 DNS、TCP、UDP、IP、ICMP、ARP 这些最基础的你要知道!
        至少要知道 这几个协议是干嘛用的! 

            DNS :  把域名解析成IP
            TCP:   安全可靠但是慢的
            UDP:   不可靠但是快
            IP:    地址....
            ICMP:  Ping 用到
            ARP:   对应 MAC地址 和 IP地址


    🔸 网络设备对应OSI层次 

        二层交换 ➜ 数据链路层 ➜ 交换机通过 Mac地址来实现数据转发
        三层路由 ➜ 网络层     ➜ 路由器用过 IP 来实现数据转发.



    🔸 路由/网关 区别 (可选)

        民用的路由器中 同时包含了 路由 和 网关两个功能. 但是企业中一般是分开的! 
        企业的思科路由器是有两三个台式电脑主机那么大的! 
        企业的网关么 和民用的路由器差不多大小.

        网关就是一个关口. 通往另一个网络.
        电脑设置网络为什么要填网关, 就是为了区分内外网络.
        你家的路由器只负责你家里面设备的相互通信. 也就是内网的通信.
        那么外网咋办呢.  所有不是内网的通信 都扔给网关.... 网关就是这个用的...
        网关的速度就是外网的速度.  光纤也就1000M. 也就一根光纤.  压力不大. 所以设备也不大

        但是企业里面几百上千台电脑.  内网网速虽然也是1000M, 但是电脑多啊! 
        上班大家都是一起用的电脑.  如果频繁的传文件, 频繁的数据备份什么的. 其实压力非常大! 
        由于内网的数据都是 路由器处理的. 所以专业的路由器体积自然就非常大了 



    🔸 企业基本网络架构
        
        不管多么复杂的网络. 整体架构都是差不多的. 

        用户 ➜ 普通交换机 ➜ 核心交换机  ➜  路由器 ➜  防火墙
            - 普通电脑接到普通交换机上.
            - 服务器等重要电脑接到核心交换机上 甚至 路由器上.



🔵 常用命令

    ipconfig   ➜ 本机IP 掩码 网关 
    ping       ➜ 测试连通性 
    nslookup   ➜ 测试是否能解析某个网址. 用来判断 DNS 是否可用!
    traceroute ➜ 路由追踪 , 可用MTR, 用来判断那个节点出错了.
    arp -a     ➜ 查看 arp 表是否正常.  有没有被 ARP 攻击! 




🔵 数据走向

    网络排错, 你首先必须要知道网络数据是怎么走的. 
    先到那个交换机, 再到那个核心交换机, 再到路由器那个口.... 
    这也是 为什么必须先了解 企业架构了.. 就是让你了解这些东西的...



🔵 基本思路

    1. 物理线路
    2. 本机网络设置: IP 掩码 网关 DNS 
    3. 测试路由/网关 畅通情况.
    4. Ping测试 内网IP + 外网IP
    5. 测试DNS  Ping 网址就行











🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 数据库 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸
                                  关系型 / 非关系型

🔵 MySQL 

🔸 主从同步原理. 



🔸 生产情况数据库是如何备份的.



🔸如何实现增量备份 及 恢复



🔸 Mysql 常用的存储引擎 以及区别 ; 工作中如何选择引擎.










增删查改

主从 主主 

读写分离 

高可用

分区分表





🔵 Redis 








🔵 MongoDB 




🔵 PostgreSQL 




🔵 SparkSQL 





🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 常见端口 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸


🔸 21: FTP File Transfer Protocol 文件传输协议.  两电脑之间实现文件上传下载


🔸 22 & 23

    • 22: SSH   
    • 23: Telnet 远程登录. 明文的! 不安全. 一般windows上用的多.


🔸 25、110 & 143

    • 25 : SMTP ➜ 发邮件 
        simple Mail Transfer Protocol. 简单邮件传输协议.  发邮件用.
        利用25端口就可以找到邮件服务器,黑掉后就可以用来转发垃圾邮件.

    • 110: POP3 ➜ 接收邮件,客户端的操作不影响服务器.
    • 143: IMAP ➜ 接收邮件,客户端的操作同步到服务器!

🔸 465、995 & 993

    • 465: SMTPS 加密的 smtp
    • 995: POP3S 加密的 pop3
    • 993: IMAPS 加密的 imap


🔸 53: DNS, 域名服务器.

🔸 873: rsync 

🔸 3306 MySQL





🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸


🔵 OSI 七层

    二层交换,三层路由!

    四层: 传输层: TCP/UDP
    三层: 网络层: IP、ICMP、ARP、RARP
    二层: 数据链路层: 



🔵 三次握手、四次挥手

    ★★★★★ https://github.com/jawil/blog/issues/14

    🔸 手动描述1 
        「你瞅啥？」
        「瞅你咋地？」
        「来咱俩唠唠。」
        然后就唠上了。


    🔸 生动描述2
        how  are you ?
                                fine.And you?
        Fine.

        俩人见面，客套完确认对方正常以后，就开始工作了。












🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 TCP UDP 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸




🔸 TCP/UDP 区别 ✔︎ 

    TCP 在传数据前必须先建立连接. 也就是三次握手,四次挥手
    TCP 连接建立后, 有数据重传、流量控制等等功能, 所以是非常可靠的.
    TCP 协议能正确处理丢包问题, 保证对方接收到完整的数据.

    UDP 在传输数据的时候是不管对方的, 只负责把数据发出去,不管对方是否收到.所以是不可靠的.

    TCP 注重数据安全性, UDP注重传输速度! 各有优点

    像DNS查询这种 要的就是速度,所以就是UDP

    各种视频网站好像用的是HTTP协议,而不是UDP, 不太确定的就不要说出来!

    当网络差的时候, TCP 会非常明显的能感觉到, UDP 的话影响小很多!




🔸 TCP 应用场景 ✔︎

    SSH、HTTP、HTTPS....

    iMessage 是端到端的加密. 绝对是TCP.




🔸 UDP 应用场景 ✔︎

    • DNS  (53端口)
    • NTP  时间同步,
    • DHCP 路由器经常会广播自己的IP地址的,这里用的也是UDP
    • SNMP 简单网络管理协议, 也是用的 UDP.

    翻墙! 就是UDP的一个经典场景.
    被墙是因为TCP被重置! 导致连接断开!一旦发送一个reset,起码会导致几分钟内不正常.
    这时候用UDP, 由于UDP本身就是无连接的,没法被重置的!
    那个 IPsec的VPN 好像用的就是 UDP,




















🔵 Socket 









🔸










🔸









🔸













🔸


🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 Misc 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

写一个防火墙配置脚本，只允许远程主机访问本机的80端口。







🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 安全 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

🔵 如何防止 DDOS 




🔵 如何防止黑客入侵, 安全防护







🔵 你用过那些LVS ,并讲述LVS各个模式的特点和区别？   【







🔵 一千万 并发，你有那些方案？【提示这些单用LVS 成受不起的，】【送五分】







🔵讲述你如何做系统优化,提高系统性能，充分利用资源？  【系统优化题目】 【送三分】








🔵八 IO 性能不足，你如何优调？   【系统优化题目】  【送三分】











🔵九 LNMP 架构优化 优化那些 ，特别影响性能那些参数,?  【应用优化题目】【提示 一定要按大并发】 【送三分】





十 如何 MySQL 优化                【应用优化题目】【提示 一定要按大并发】 【送三分】


十一 讲术 Memecahe 工作原理和优缺？【送二分】


十二 讲术CDN工作原理和优缺？ 【送二分】


十三 你如何监视服务器质量和网络质量？用个那些工具 及优缺点？【送二分】





















🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸 Linux 🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸







