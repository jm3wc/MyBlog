Linux基础

> ## 什么是Linux

 Linux是类Unix计算机操作系统的统称。Linux操作系统的内核名字也是“Linux”。Linux操作系统也是自由软件和开发源代码发展中最著名的例子。严格来说，Linux这个词只表示Linux内核，但是在实际上人们已经习惯了用Linux来形容整个基于Linux内核，并且使用GNU工程各种工具和数据库的操作系统。Linux得名于计算机业余爱好者Linus Torvalds。

 Linux是一套免费使用和自由传播的类Unix操作系统，它主要用于基于Intel x86系列CPU的计算机上。这个系统是由世界各地的成千上万的程序员设计和实现的。其目的是建立不受任何商品化软件的版权制约的、全世界都能自由使用的Unix兼容产品。

> #### Linux 历史篇

##### Multics 的计划

```php
1965年前后,由贝尔实验室 (Bell)、麻省理工学院(MIT) 及美国通用电气公司 (GE) 共同发起.
Multics其目的是想要让大型主机可以达成提供 300 个以上的终端机连线使用的目标.
后来因计画进度落后，资金短缺，宣告失败。
```

##### Unics

```php
1969 年Multics 的计划的成员贝尔实验室的肯·汤普逊(Ken Thompson)
利用一部 dec (digital equipment corporation) 的 pdp-7 ，以汇编语言 (Assembler)写出了一个核心程式.
同时包括一些核心工具程式,以及一个档案系统，这个系统就是 unix 的原型，称为Unics 。
```

#### Unix

```php
1973 年。贝尔实验室的肯·汤普逊(Ken Thompson)跟丹尼斯·里奇(Dennis Ritchie,C语言之父)重新以 c 语言改写.
最后发行成 Unix 。
```

#### BSD

```php
Unix 后来与加州柏克莱(Berkeley)大学合作,1977年柏克莱大学的 Bill Joy 著手修改成适合自己机器的版本.
并且同时增加了很多工具软体与编译程式，命名為 Berkeley Software Distribution (BSD) .
这个 BSD 是 unix 很重要的一个分支（Bill Joy也是著名业者 SUN这家公司的创办者）.
```

#### Minix

```php
1986年荷兰阿姆斯特丹自由大学谭邦宁教授(Andrew S Tanenbaum)完成 minix 这个 unix like 的核心程式，将 unix 改写并移植到 x86 结构上面
```

#### GNU计划

```php
1984 年理查德·马修·斯托曼(Richard Stallman) 发起GNU计划(GNU 是 GNU's Not Unix 的缩写)
并且成立自由软件基金会对於现今的自由软件风潮，有著不可磨灭的功劳.
```

#### GPL

```
1985年，為了避免GNU所开发的自由软件被其他人所利用而成為专利软件.
Stallman与律师草拟了有名的通用公共许可证GPL(General Public License) .其特点為：

1.可以根据自己的需求來执行這個自由软件
2.可以自由的复制该软件
3.可以將取得的原始码進行程式修改工作
4.可以將您修改過的程式，再度的自由發行
5.应该將您修改過的程式码回馈于社会
6.不能將一個 GPL 授权 的自由软件，在修改後取消 GPL 授权
7.不能单纯的贩卖自由软件（需提供售后服务与相关手册等）
```

#### Linux

```
1991年10月5日，芬兰赫尔辛基的大學生Linus Torvalds(林纳斯·托瓦兹) 
在comp.os.minix 這個新闻群组上发布了 0.02版Linux。
“有些人生来就具有统率百万人的领袖风范；另一些人则是为写出颠覆世界的软件而生。
唯一一个能同时做到这两者的人
就是托瓦兹.” 美国《时代》周刊对“Linux之父”林纳斯·托瓦兹（Linus Torvalds）给出了极高的评价。
```

#### 发行版

```php
那么，什么是发行版呢？因为Linux是开源项目，它的源代码是放到网络上.
让世界各地的人们去下载，那么有些人在拿到Linux之后就会修改成自己喜欢的 Linux版本，
而当他公布了自己修改完的版本到网络上面，那么就是所谓的发行版了。
时至今日，Linux已经出现了很多很多的好用版本，如果你不知道使用那些版本的话.
你可以使用一些比较出名的Linux发行版.
例如：Centos、Ubuntu、openSUSE、Fedora、SElinux.
其中CentOS是在服务器端是出了名的稳定的，还有Ubuntu重点是放在个人桌面系统领域。
```

![img](http://web.wdwangke.com/mdphoto/backend/backend/linux.png)

## VMware虚拟机安装

> #### 安装前述

```php
如果你想玩下Linux系统，那么你有两种选择.
第一种选择就是直接在你自己的电脑上安装，我们通常会把这种叫真实电脑安装，为什么呢？
因为第二种选择是在虚拟机上安装Linux，我们会把这种叫做虚拟机安装。
那么，什么是虚拟机？其实虚拟机只是一款软件，而这款软件的功能是模拟真实电脑.
虚拟一台假电脑提供给使用者安装系统之用.
这样做的好处就是我们完全可以不用先删除自己现有的系统，就可以玩上Linux.
当然也是可以玩其他系统的。
```

> #### 安装准备

```php
1.VMware （推荐使用的一款虚拟机软件）
```

1、双击VMware安装程序后会弹出一个安装向导的窗口，然后我们点击下一步

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/VMware_1.png)

2、这是VMware的许可协议，按图操作即可

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/VMware_2.png)

3、VMware的安装路径默认安装在C盘，我们改成任意个盘，例如D盘。然后下一步

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/VMware_3.png)

4、体验设置，一般默认即可，然后我们下一步

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/VMware_4.png)

5、选择是否在桌面创建快捷方式和开始菜单创建文件夹与快捷方式

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/VMware_5.png)

6、因为图中的是已经安装过VMware了，所以点击中间的升级那个按钮

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/VMware_6.png)

7、如果你有VMware许可证，可以点许可证。没有就点完成即可

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/VMware_7.png)

8、准备好系统镜像，下面我们会到用ubuntu系统镜像

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/ubuntu_1.png)

9、打开VMware，如图操作 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/ubuntu_2.png)

10、选择安装方法，一般经典即可，再下一步

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/ubuntu_3.png)

11、这里选择镜像，然后下一步

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/ubuntu_4.png)

12、这步就根据自己的需求去设置图下的选项

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/ubuntu_5.png)

13、虚拟机名称和该虚拟机的位置，有需要就改，没有就默认

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/ubuntu_6.png)

14、这里给虚拟机配置磁盘大小，默认的是20g

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/ubuntu_7.png)

15、给虚拟机配置硬件，例如CPU的核数和运行内存等等，然后点击完成，等待开机

## Centos系统安装

#### 什么是Centos

```php
CentOS是Community Enterprise Operating System的缩写，也叫做社区企业操作系统。
是企业Linux发行版领头羊Red Hat Enterprise Linux（以下称之为RHEL）的再编译版本（是一个再发行版本），
而且在RHEL的基础上修正了不少已知的 Bug ，相对于其他 Linux 发行版，其稳定性值得信赖。

下面会讲解如何安装CenteOS
```

#### 安装前准备

```
1.VMware （推荐使用的一款虚拟机软件）
2.CentOS系统镜像
```

#### 文件下载

[**系统镜像与VMware软件**](https://www.aliyundrive.com/s/GDps6jKYNwM)

**密码：g9e7**

#### 安装步骤

1. VMware软件与系统镜像安装可以参考VMware虚拟机安装这章节

2. 安装完开启centos系统会出现一个界面，如下

   ```php
   参数说明
   
   Install CentOS 7 安装CentOS 7 (选择该项)
   Test this media & install CentOS 7 测试安装文件并安装CentOS 7
   Troubleshooting 修复故障
   ```

   ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_1.png)

3. 这里选择第一项，安装CentOS 7，回车，进入下面的界面。选择语言：中文-简体中文（中国）(这是安装时的语言)

   ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_3.png)

4. 点击继续，会有一个界面，然后选择网络和主机名

   ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_4.png)

5. 选择后会出现如下界面，把以太网打开然后完成

   ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_5.png)

6. 点击开始安装，会出现如下界面，注意在这步必须要设置root密码，图里显示已经设置了。可以创建新的用户也不用创建，但是建议创建一个新的用户

   ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_6.png)

7. 设置root密码，由于密码太简单了，需要点击两次完成

   ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_7.png)

8. 创建用户，由于密码太简单了，需要点击两次完成

   ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_8.png)

9. 已经设置root密码以及创建好用户，最后一步点击重启

   ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_9.png)

10. 选择重启后开机会出现一个界面，选择第一项

    ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_10.png)

11. 选择用哪个用户开机，这里选的是root超级管理员，注意这里输入密码是不显示出来

    ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/centos_11.png)

12. 配置网卡，因为centOS7开机不会自动开启网卡，所以需要去修改一下配置文件

    ```php
    // 一、查看ip以及网卡，由于centos没有安装net-tools，所以ifconfig使用不了
    ip addr
    
    // 二、执行ip addr指令后会会返回以下信息，如果ens33没有inet 192.168.6.12类似信息，说明网卡没有正常运行(下面信息里的ens33是正常使用的)   
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
           valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host
           valid_lft forever preferred_lft forever
    2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
        link/ether 00:0c:29:2b:b0:49 brd ff:ff:ff:ff:ff:ff
        inet 192.168.6.128/24 brd 192.168.6.255 scope global noprefixroute dynamic ens33
           valid_lft 1542sec preferred_lft 1542sec
        inet6 fe80::c9ef:8ba9:4a00:f031/64 scope link noprefixroute
           valid_lft forever preferred_lft forever
    
    // 三、修改配置网卡文件       
    vi /etc/sysconfig/network-scripts/ifcfg-ens33
    
    // 或者可以这样       
    1. cd /etc/sysconfig/network-scripts/
    2. ls // 查看当前目录有哪些文件，找到 ifcfg-网卡名 例如这里ifcfg-ens33
    2. vi ifcfg-ens33
    
    // 四、打开后网卡的默认配置       
    TYPE=Ethernet
    PROXY_METHOD=none
    BROWSER_ONLY=no
    BOOTPROTO=dhcp
    DEFROUTE=yes
    IPV4_FAILURE_FATAL=no
    IPV6INIT=yes
    IPV6_AUTOCONF=yes
    IPV6_DEFROUTE=yes
    IPV6_FAILURE_FATAL=no
    IPV6_ADDR_GEN_MODE=stable-privacy
    NAME=ens33
    UUID=680f0e10-9dc6-4f00-b942-888ca244d4bf
    DEVICE=ens33
    ONBOOT=no
    
    // 五、找ONBOOT选项，把no改为yes     
    ONBOOT=yes
    
    // 六、重启网卡或者重启系统      
    service network restart 或 systemctl restart netwrok
    
    // 七、测试      
    ping www.baidu.com
    ```

## SSH连接Linux服务器

一般我们连接服务器都是用ssh连接服务器，再个别一点在服务器商提供一些方法去连接。这里我们用xshell软件进行远程连接

**xshell官网**

https://www.netsarang.com/en/xshell/

**xshell免费版**

https://www.netsarang.com/zh/free-for-home-school/

> #### 安装openssh-server (注意这里用root用户，普通用户在指令前面加上sudo)

1.安装指令

```
yum install -y openssl openssh-server
```

2.执行下面的指令修改配置文件,去掉监听地址前的以及允许远程用户使用root登陆

```shell
vi /etc/ssh/sshd_config

#找到下面两行代码，把代码前面的井号去掉
# ssh的端口
#Port 22
# 允许root用户登录
#PermitRootLogin yes

# 重置root用户的密码
sudo passwd root
```

![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/ssh_1.png)

3.修改好后按键盘按键 ESC 然后输入冒号 再输入 wq 保存退出

4.ssh以及防火墙一些常用指令

```
查看防火墙
firewall-cmd --state

临时关闭防火墙
systemctl stop firewalld

临时打开防火墙
systemctl start firewalld

开机禁止启动防火墙
systemctl disable firewalld

开机启动防火墙
systemctl enable firewalld

查看状态：
systemctl status sshd.service

启动服务：
systemctl start sshd.service

重启服务：
systemctl restart sshd.service

开机自启：
systemctl enable sshd.service

开机禁用
systemctl disable sshd.service

关闭ssh服务
systemctl stop sshd.service
```

> #### xshell安装(付费版安装)

1、我们打开上面的链接,按图操作

![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_1.png)

2、打开后选择30 Day Evaluation这块，填上你的名字和你的邮箱，然后点击STARTTRIAL，你会收到一封邮件里会有下载链接，点击下载

3、点击软件包安装，首先打开后再下一步

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_2.png)

4、再到许可协议，选择我接受许可证协议中的条款

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_3.png)

5、选择安装路径，根据自己的情况去选择，再下一步

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_4.png)

6、这一步就默认即可

7、最一步点击安装，然后等待安装

8，打开xshell，点击文件再选择新建

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_5.png)

9、新建会话这里按图片去操作即可，这里我们用阿里云的服务器来测试

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_6.png)

10、输入用户名，点击确定

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_7.png)

11、输入密码，然后点击确定

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_8.png)

12、这样连接成功！

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/xshell_9.png)

## LAMP/LNMP的环境编译

> #### 什么是LAMP？什么是LNMP？

LAMP是Linux+Apache+MySQL+PHP ,LNMP就是Linux+Nginx+MySQL+PHP

> #### 什么是Nginx?

Nginx ("engine x") 是一个高性能的 HTTP 和 反向代理 服务器，也是一个 IMAP/POP3/SMTP 代理服务器。 Nginx 是由 Igor Sysoev 为俄罗斯访问量第二的 Rambler.ru 站点开发的。Igor 将源代码以类BSD许可证的形式发布。Nginx 已经因为它的稳定性、丰富的功能集、示例配置文件和低系统资源的消耗而闻名了。 官方网站：http://nginx.org/

> #### 安装篇

现在我们一般都使用集成环境，很少使用自定义环境，因为能大大节省了搭建php mysql环境的时间，我们安装好就可以直接使用。

这里我们主要搭建宝塔的集成环境，当然，还有其他的集成环境 例如phpstudy linux版等等

> #### 其他集成环境

https://lnmp.org/

https://www.wdlinux.cn/wdcp/

https://www.xp.cn/linux.html#install-show

> #### 安装宝塔

1、我们去Linux系统(Ubuntu)里面，在桌面点击鼠标右键选择在终端打开(因为搭建环境用的系统是Ubuntu有桌面)

2、在终端输入su，输入密码，如果忘记密码了，在终端输入sudo passwd root重设置密码

3、去浏览器打开宝塔官网https://www.bt.cn/ 选Linux版

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/bt_1.png)

4、我们根据我们的系统选择，复制命令去终端里回车，等待安装完成

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/bt_2.png)

5、安装完成后，终端会弹出宝塔工具箱界面和内网和外网IP，按需求选择命令

6、如果忘记内网和外网的IP，可以在终端输入bt default

7、如果需要宝塔工具箱，在终端里输入bt

7、首次进入宝塔面板时会有一个弹窗，让我们选择LAMP还是LNMP的环境

8、可以在面板里软件商店按需求安装要的插件

9、新建站点，按图下的操作，每个项目的端口要不一样的端口，不然访问不了

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/bt_3.png)

10、配置好了就在浏览器输入内网ip+端口就可以访问

## Linux文件处理命令

在Linux系统里我们一般都是用命令行去操作。不会像Windows可视图操作

> #### 文件操作

## 1、ls 显示文件

```
    -a    显示所有文件(包括隐藏的文件)
    -l    显示文件的详细信息
    -h    易读模式(带单位)
    -u    显示文件的最后访问时间
    -t    按时间排序显示

显示的结果中,第一个字符一般用来区分文件和目录：
d：表示是一个目录，事实上在ext2fs中，目录是一个特殊的文件。
－：表示这是一个普通的文件。
l: 表示这是一个符号链接文件，实际上它指向另一个文件。
例1：显示当前工作目录的文件
    ls -l
例2：显示当前www目录下所有文件
    ls -l /var/www
```

## 2、cd 切换目录

```
    cd  [绝对路径或相对路径]

    cd -    返回前一个工作目录
    cd .    进入当前工作目录
    cd ..    返回上一级工作目录
    cd ~    返回当前用户家目录
```

## 3、pwd 查看当前工作目录

```
    pwd
```

## 4、mkdir 创建目录

```
    mkdir  [-mp]  目录名称
    -m        设置目录权限
    -p        递归创建目录
```

## 5、rmdir 删除目录

```
    rmdir 目录名（只能删空的文件夹）
```

## 6、cp 复制文件

```
    cp [-adfilprsu] 来源文件 目标文件
    -r 递归复制
    -p 连同文件属性一起复制，包括权限、所有者和时间等
    -f 强行复制
```

## 7 、mv 移动或重命名

```
    mv file1(文件) file2(文件)  将源文件名 file1 改为目标文件名 file2
    mv source_file(文件) dest_directory(目录)  将文件 source_file 移动到目标目录 dest_directory 中
    -b: 当目标文件或目录存在时，在执行覆盖前，会为其创建一个备份。
    -i: 如果指定移动的源目录或文件与目标的目录或文件同名，则会先询问是否覆盖旧文件，输入 y 表示直接覆盖，输入 n 表示取消该操作。
    -f: 如果指定移动的源目录或文件与目标的目录或文件同名，不会询问，直接覆盖旧文件。
    -n: 不要覆盖任何已存在的文件或目录。
    -u：当源文件比目标文件新或者目标文件不存在时，才执行移动操作。
```

## 8、rm 删除文件

```
    -r   递归删除
    -f    强制删除
```

## 9、touch 创建文件或者修改文件的属性

```
    例：#touch –t 201008081230 hello.txt  修改文件时间
    -a 改变档案的读取时间记录。
    -m 改变档案的修改时间记录。
    -c 假如目的档案不存在，不会建立新的档案。与 --no-create 的效果一样。
    -f 不使用，是为了与其他 unix 系统的相容性而保留。
    -r 使用参考档的时间记录，与 --file 的效果一样。
    -d 设定时间与日期，可以使用各种不同的格式。
    -t 设定档案的时间记录，格式与 date 指令相同。
    --no-create 不会建立新档案。
    --help 列出指令格式。
    --version 列出版本讯息。
```

## 10、cat 查看文件

```
    cat a.html                          查看文件内容
    cat a.html b.html > c.html          合并多个文件的内容写入到新建的文件
    cat a.html b.html >> c.html         合并多个文件的内容追加到指定文件
    cat -n c.html                       查看文件内容（有行号）
    cat /dev/null > a.html              清空一个文件的内容
    cat -b a.html                       查看文件内容（有行号，不包括空白行）
    cat -s a.html                       查看文件内容（有行号，合并连续的空白行）
    cat -E a.html                       查看文件内容（每行结尾处添加$符号）
    cat a.html b.html                   同时查看多个文件的内容
```

## Linux权限管理命令

> #### 什么是权限管理

就像有某些目录或者文件没有访问权限时，这时候我们用到linux的命令去改变它们的访问权限，还有用户与用户组管理

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/linux/root.png)

#### 一、chmod 改变文件或目录的权限

```
    -u 表示该文件的拥有者，g 表示与该文件的拥有者属于同一个群体(group)者，o 表示其他以外的人，a 表示这三者皆是。
    + 表示增加权限、- 表示取消权限、= 表示唯一设定权限。
    -r 表示可读取，w 表示可写入，x 表示可执行，X 表示只有当该文件是个子目录或者该文件已经被设定过为可执行。
其他参数说明：

    -c : 若该文件权限确实已经更改，才显示其更改动作
    -f : 若该文件权限无法被更改也不要显示错误讯息
    -v : 显示权限变更的详细资料
    -R : 对目前目录下的所有文件与子目录进行相同的权限变更(即以递归的方式逐个变更)
    --help : 显示辅助说明
    --version : 显示版本
```

###### 1、权限数字表示方式

```
    r:4        w:2    x:1
    如：-rwxr-xr--     =    [4+2+1][4+0+1][4+0+0]=754 
    例1：开放文件所有权限
    # chmod      777  .bashrc
```

##### 2、符号方式改变权限

| who  | 用户类型 |        **说明**        |
| :--: | :------: | :--------------------: |
|  u   |   user   |       文件所有者       |
|  g   |  group   |    文件所有者所在组    |
|  o   |  others  |      所有其他用户      |
|  a   |   all    | 所用用户, 相当于 *ugo* |

```
    例1：将文件权限设置为：拥有者具有所有权限，群组、其它人具有可读、可执行权限
    # chmod u=rwx,go=rx .bashrc 

    例2：去掉全部人的可执行权限
    # chmod a-x .bashrc
```

#### 二、chgrp 改变群组

```
    chgrp [-R]  用户名     文件名
    -R:进行递归的修改，即连同子目录下的所有文件都会修改
    例：
    #chgrp  –R   www    /var/www 

    3.chown 改变文件拥有者
    chown [-R] 用户名 文件或目录
    chown [-R] 用户名:组名 文件或目录

    例：
    #chown    -R   www:www    /var/www
```

#### 三、sudo 给运行的命令以root特权

```
sudo apt-get update  更新源

sudo apt-get remove package 删除安装包

sudo apt-get install package 安装包
```

## Linux文件搜索命令

## 1、find

```
    find是最常见和最强大的查找命令，你可以用它找到任何你想找的文件。
    find <指定目录> <指定条件> <指定动作>

　　    
　　    
　　    例：
　　        find /home -name 'my*'  搜索当前目录（含子目录，以下同）中，所有文件名以my开头的文件。
　　        find /home -name 'my*' -ls  搜索当前目录中，所有文件名以my开头的文件，并显示它们的详细信息。
　　        find /home -type f -mmin -10    搜索当前目录中，所有过去10分钟中更新过的普通文件。如果不加-type f参数，则搜索普通文件+特殊文件+目录
```

## 2、which

```
    在PATH变量指定的路径中，搜索某个系统命令的位置，并且返回第一个搜索结果

    例：
        which grep
        which  ls
```

## 3、whereis

```
查看文件的位置

例：
    whereis  ls
```

## Linux压缩解压编译命令

Linux的压缩解压都是通过命令行执行，不像Windows有各种各样的压缩解压软件，所以我们要学习该命令

## 1、zip 压缩

```
    zip 压缩文件名 要压缩的文件
    压缩单个文件
    zip web.zip a.html
    zip web.zip ./a.html

    压缩多个文件
    zip web.zip a.html b.html
    zip web.zip ./a.html ./b.html

    压缩目录
    -r是启动递归，将目录下的所有文件全部压缩到web.zip里面
    zip -r web.zip casepro
    zip -r web.zip ./casepro

    从压缩文件里面删除文件
    zip -d web.zip a.html

    移动文件到压缩文件里面。注意：会删除源文件的
    zip -m web.zip c.html
```

## 2、unzip 解压缩

```
    显示压缩文件内所包含的文件
    unzip -l web.zip
    unzip -l ./web.zip

    不必先询问用户，unzip执行后覆盖原有文件
    unzip -o web.zip
    unzip -o ./web.zip

    指定文件解压缩后所要存储的目录
    unzip -d web web.zip
    unzip -d ./web ./web.zip
```

## 3、tar 压缩/解压

```
    tar [参数] [压缩文件名] [要压缩的文件]
    -z 亦即是否需要用 gzip 压缩或解压？
    -c 建立压缩文件
    -v 显示处理过程
    -f 使用创建的压缩文件
    tar -zcvf web.tar.gz a.html b.html

    tar [参数] [解压缩文件名]
    -z 亦即是否需要用 gzip 压缩或解压？
    -x 提取压缩文件内的文件
    -v 显示处理过程
    -f 使用创建的压缩文件
    tar -zxvf web.tar.gz

    tar [参数] [tar文件名]
    -t 列出归档内容
    -v 详细地列出处理的文件
    -f 使用的压缩文件
    tar -tvf web.tar.gz
```

## Linux文本编辑器Vim的使用

Vim是从 vi 发展出来的一个文本编辑器。代码补完、编译及错误跳转等方便编程的功能特别丰富，在程序员中被广泛使用。

vim 的官方网站 ([http://www.vim.org](http://www.vim.org/))

```
vi/vim 共分为三种模式:
    命令模式（Command mode）
    输入模式（Insert mode）
    底线命令模式（Last line mode）
```

#### 命令模式：

```
    刚启动 vi/vim，便进入了命令模式。

    此状态下敲击键盘动作会被Vim识别为命令，而非输入字符。比如我们此时按下i，并不会输入一个字符，i被当作了一个命令。

    以下是常用的几个命令：

    i 切换到输入模式，以输入字符。
    x 删除当前光标所在处的字符。
    : 切换到底线命令模式，以在最底一行输入命令。
    若想要编辑文本：启动Vim，进入了命令模式，按下i，切换到输入模式。

    命令模式只有一些最基本的命令，因此仍要依靠底线命令模式输入更多命令。
```

#### 输入模式:

```
    输入模式
    在命令模式下按下i就进入了输入模式。

    在输入模式中，可以使用以下按键：

    字符按键以及Shift组合，输入字符
    ENTER，回车键，换行
    BACK SPACE，退格键，删除光标前一个字符
    DEL，删除键，删除光标后一个字符
    方向键，在文本中移动光标
    HOME/END，移动光标到行首/行尾
    Page Up/Page Down，上/下翻页
    Insert，切换光标为输入/替换模式，光标将变成竖线/下划线
    ESC，退出输入模式，切换到命令模式
```

#### 底线命令模式:

```
    在命令模式下按下:（英文冒号）就进入了底线命令模式。

        底线命令模式可以输入单个或多个字符的命令，可用的命令非常多。

        在底线命令模式中，基本的命令有（已经省略了冒号）：

        q 退出程序
        w 保存文件
        按ESC键可随时退出底线命令模式。
    vim test.txt    vi 来建立一个名为 test.txt 的文件
    请注意，记得 vi 后面一定要加文件名，不管该文件存在与否
```

 ![img](http://web.wdwangke.com/mdphoto/backend/backend/vim.png)