## 1.2 分层

|        | 作用                             | 例子                  |
| :----- | :------------------------------- | :-------------------- |
| 应用层 | 处理特定的应用程序细节           | Telnet、FTP和e-mail等 |
| 运输层 | 为主机的应用程序提供端到端的通信 | TCP和UDP              |
| 网络层 | 处理分组在网络中的活动           | IP、ICMP、IGMP        |
| 链路层 | 处理与电缆的物理接口细节         | 设备驱动程序及接口    |

![1. 概述 - 图1](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap1/img1.png)

大多数的网络应用程序都被设计成客户 - 服务器模式。应用程序是一个用户进程，下三层工作在内核中。下三层对应用程序一无所知，但它们要处理所有的通信细节。

网络层IP提供的是一种不可靠的服务。也就是说，它只是尽可能快地把分组从源结点送到目的结点，但是并不提供任何可靠性保证。而另一方面，TCP在不可靠的IP层上提供了一个可靠的运输层。为了提供这种可靠的服务，TCP采用了超时重传、发送和接收端到端的确认分组等机制。

构造互联网最简单的方法是使用路由器，它可以为不同类型的物理网络提供链接：以太网、令牌环网、点对点的链接和FDDI（光钎分布式数据接口）等等。

连接网络的另一个途径是使用网桥。网桥是在链路层上对网络进行互连，而路由器则是在网络层上对网络进行互连。网桥使得多个局域网（LAN）组合在一起，这样对上层来说就好像是一个局域网。

## 1.3 TCP/IP的分层

![1. 概述 - 图2](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap1/img2.png)

ICMP是IP协议的附属协议，IP层用它来与其他主机或路由器交换错误报文和其他重要信息。

## 1.4 互联网的地址

互联网上的每个接口必须有一个唯一的Internet地址（也称作IP地址）。IP地址长32bit。

![1. 概述 - 图3](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap1/img3.png)

| 类型 | 范围                        |
| :--- | :-------------------------- |
| A    | 0.0.0.0 - 127.255.255.255   |
| B    | 128.0.0.0 - 191.255.255.255 |
| C    | 192.0.0.0 - 223.255.255.255 |
| D    | 224.0.0.0 - 239.255.255.255 |
| E    | 240.0.0.0 - 255.255.255.255 |

分配IP地址的机构是互联网络信息中心（InterNIC）。

有三类IP地址：

1. 单播地址（单个主机）
2. 广播地址（给定网络上的所有主机）
3. 多播地址（同一组内的所有主机）

## 1.5 域名系统

在TCP/IP领域中，域名系统（DNS）是一个分布的数据库，由它来提供IP地址和主机名之间的映射信息。

## 1.6 封装

当应用程序用TCP传送数据时，数据被送入协议栈，逐个通过每一层直到被当做一串比特流送入网络，每一层对收到的数据都要增加一些头部信息（尾部信tp息）。

TCP传送给IP的数据单元称为TCP报文段，UDP称为为UDP数据报，IP传送给网络接口层的称为IP数据报，以太网传输的比特流称为帧。

IP首部有个8bit的数值称为协议域，标志数据属于哪一层。1标识ICMP，2标识IGMP，6标识TCP，17标识UDP。

以太网数据帧的物理特性是其长度必须在46 - 1500字节之间。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap1/img4.png)

## 1.7 分用

当目的主机收到一个以太网数据帧时，数据就开始从协议栈中由底向上升，同时去掉各层协议加上的报文首部。每层协议盒都要去检查报文首部中的协议标识，以确定接收数据的上层协议。这个过程称作分用。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap1/img5.png)

## 1.8 客户-服务器模型

重复型或并发型。重复型服务器通过以下步骤进行交互：

I1. 等待一个客户请求的到来。

I2. 处理客户请求。

I3. 发送响应给发送请求的客户。

I4. 返回I1 步。

重复型服务器主要的问题发生在I2状态。在这个时候，它不能为其他客户机提供服务。

相应地，并发型服务器采用以下步骤：

C1. 等待一个客户请求的到来。

C2. 启动一个新的服务器来处理这个客户的请求。在这期间可能生成一个新的进程、任务或线程，并依赖底层操作系统的支持。这个步骤如何进行取决于操作系统。生成的新服务器对客户的全部请求进行处理。处理结束后，终止这个新服务器。

C3. 返回C1步。

TCP服务器是并发的，而UDP服务器是重复的

## 1.9 端口号

TCP和UDP采用16bit的端口号来识别应用程序。服务器一般都是通过知名端口号来识别的。客户端通常对它所使用的端口号并不关心，只需保证该端口号在本机上是唯一的就可以了。

UNIX也有保留端口号，分配给拥有超级用户特权的进程。

## 1.15 应用编程接口

使用TCP/IP协议的应用程序通常采用两种应用编程接口（API）：socket和TLI（运输层接口： Transport Layer Interface）。

## 链路层

链路层主要有三个目的：

（1）为IP模块发送和接收IP数据报；

（2）为ARP模块发送ARP请求和接收ARP应答；

（3）为RARP发送RARP请求和接收RARP应答。

TCP/IP支持多种不同的链路层协议，这取决于网络硬件，如以太网、令牌环网、FDDI和RS-232串行线路等。

## 2.2 以太网和 IEEE 802封装

以太网是当今TCP/IP采用的主要的局域网技术。它采用一种称作CSMA/CD的媒体接入方法，其意思是带冲突检测的载波侦听多路接入（Carrier Sense, Multiple Access with Collision Detection）。它的速率为 10 Mb/s，地址为48 bit 。

| 802.3 | CSMA/CD网络  |
| :---- | :----------- |
| 802.4 | 令牌总线网络 |
| 802.5 | 令牌环网络   |

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap2/img1.png)

两种帧格式都采用48bit（6字节）的目的地址和源地址。在802标准定义的帧格式中，长度字段是指它后续数据的字节长度，但不包括 CRC检验码。以太网的类型字段定义了后续数据的类型。

802定义的有效长度值与以太网的有效类型值无一相同，这样，就可以对两种帧格式进行区分。

## 2.4 SLIP：串行线路IP

SLIP的全称是Serial Line IP 。它是一种在串行线路上对IP数据报进行封装的简单形式。

下面的规则描述了SLIP协议定义的帧格式：

1) IP数据报以一个称作END（0xc0）的特殊字符结束。为了防止数据报到来之前的线路噪声被当成数据报内容，大多数实现在数据报的开始处也传一个END字符。

2) 如果IP报文中某个字符为END，那么就要连续传输两个字节0xdb和0xdc来取代它。

3) 如果IP报文中某个字符为SLIP的ESC字符，那么就要连续传输两个字节0xdb和0xdd来取代它。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap2/img2.png)

SLIP的缺陷：

1) 每一端必须知道对方的IP地址。没有办法把本端的IP地址通知给另一端。

2) 数据帧中没有类型字段（类似于以太网中的类型字段）。如果一条串行线路用于SLIP，那么它不能同时使用其他协议。

3) SLIP没有在数据帧中加上检验和，只能通过上层协议来实现。

由于串行线路的速率较低，且通信常是交互式的，因此在SLIP线路上有许多小的TCP分组进行交换，这就带来了性能的缺陷。CSLIP是压缩的SLIP，它能把40个字节压缩到3-5个字节。

## 2.6 PPP：点对点协议

PPP，点对点协议修改了SLIP协议中的所有缺陷。 PPP包括以下三个部分：

1) 在串行链路上封装IP数据报的方法。PPP既支持数据为 8位和无奇偶检验的异步模式，还支持面向比特的同步链接。

2) 建立、配置及测试数据链路的链路控制协议（LCP：LinkControl Protocol ）。它允许通信双方进行协商，以确定不同的选项。

3) 针对不同网络层协议的网络控制协议（NCP）体系

每一帧都以标志字符0x7e开始和结束。紧接着是一个地址字节，值始终是0xff，然后是一个值为0x03的控制字节。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap2/img3.png)

由于标志字符的值是0x7e，因此当该字符出现在信息字段中时， PPP需要对它进行转义。在同步链路中，该过程是通过一种称作比特填充 (bit stuffing)的硬件技术来完成的。

PPP比SLIP 具有下面这些优点：

(1) PPP支持在单根串行线路上运行多种协议，不只是 IP协议；

(2) 每一帧都有循环冗余检验；

(3) 通信双方可以进行IP地址的动态协商 (使用IP网络控制协议 )；

(4) 与CSLIP类似，对 TCP和IP报文首部进行压缩；

(5) 链路控制协议可以对多个数据链路选项进行设置。

## 2.7 环回接口

大多数的产品都支持环回接口（Loopback Interface），以允许运行在同一台主机上的客户程序和服务器程序通过TCP/IP进行通信。A 类网络号127就是为环回接口预留的。根据惯例，大多数系统把 IP地址127.0.0.1 分配给这个接口，并命名为localhost。一个传给环回接口的IP数据报不能在任何网络上出现。

一旦传输层检测到目的端地址是环回地址时，应该可以省略部分传输层和所有网络层的逻辑操作。但是大多数的产品还是照样完成传输层和网络层的所有过程，只是当IP数据报离开网络层时把它返回给自己。

需要指出的关键点：

1. 传给127.0.0.1的任何数据君合作为IP输入。
2. 传给广播地址或多播地址的数据报复制一份传给127.0.0.1，然后送到以太网上。
3. 任何传给该主机IP地址的数据均送到127.0.0.1。

## 2.8 最大传输单元 MTU

以太网和802.3对数据帧的长度都有一个限制，其最大值分别是1500和1492字节。链路层的这个特性称作MTU，最大传输单元。

## 2.9 路径 MTU

两台通信主机路径中的最小 MTU，路径MTU 在两个方向上不一定是一致的。

## IP：网络协议

IP提供的是不可靠、无连接的数据报传送服务：

1. 不可靠的意思是它不能保证IP数据报能成功地到达目的地。IP仅提供最好的传输服务。如果发生某种错误时，如某个路由器暂时用完了缓冲区，IP有一个简单的错误处理算法：丢弃该数据报，然后发送ICMP消息报给信源端。任何要求的可靠性必须由上层来提供（如TCP）。
2. 无连接的意思是IP并不维护任何关于后续数据报的状态信息。每个数据报的处理是相互独立的。这也说明，IP数据报可以不按发送顺序接收。

## 3.2 IP首部

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap3/img0.png)

传输数据之前把首部转换成网络字节序：注意大端和小端。

首部长度 指的是首部占32 bit字的数目，包括任何选项。由于它是一个4比特字段，因此首部最长为60个字节。

服务类型（TOS）字段包括一个3 bit的优先权子字段（现在已被忽略），4 bit的TOS子字段和 1 bit未用位但必须置0。4 bit的TOS分别代表：最小时延、最大吞吐量、最高可靠性和最小费用。

总长度字段 是指整个IP 数据报的长度，以字节为单位。由于该字段长16比特，所以IP数据报最长可达65535字节。

标识字段 唯一地标识主机发送的每一份数据报。

TTL（time - to - live）生存时间字段设置了数据报可以经过的最多路由器数。TTL初始值由源主机设置，一旦经过一个处理它的路由器，它的值就减去1。当值为0时，数据报被丢弃，并发送ICMP报文通知源主机。

首部检验和字段 是根据IP首部计算的检验和码。它不对首部后面的数据进行计算。

最后一个字段是任选项，是可变长的可选信息，定义如下：

- 安全和处理限制
- 记录路径（让每个路由器都记下它的IP）
- 时间戳（让每个路由都记下它的IP地址和时间）
- 宽松/严格的源站选录

## 3.3 IP路由选择

IP可以从TCP、UDP、ICMP、IGMP接收数据报（即在本地生成的），或者从一个网络接口接收数据报（待转发的）并进行发送。IP层在内存中有个路由表。当收到一份数据报时，它都检索一次表。当数据报来自某个网络接口时，IP首先检查目的IP地址是否为本机的IP地址之一或者IP广播地址。如果是，数据报就被送到由IP首部协议字段所指定的协议模块进行处理。如果数据报目的地址不是这些地址，那么

1. 如果IP蹭被设置成路由器的功能，那么就对数据报进行转发，否则
2. 丢弃数据报

路由表中的每一项都包含下面这些信息：

1. 目的IP地址。它既可以是一个完整的主机地址，也可以是一个网络地址，由该表目中的标志字段来指定（如下所述）。
2. 下一站（或下一跳）路由器（next-hop router）的I P 地址，或者有直接连接的网络IP地址。
3. 标志。其中一个标志指明目的 IP地址是网络地址还是主机地址，另一个标志指明下一站路由器是否为真正的下一站路由器，还是一个直接相连的接口。
4. 为数据报的传输指定一个网络接口。

IP路由选择是逐跳地进行的。从路由表信息可以看出，IP并不知道到达任何目的的完整路径（当然，除了那些与主机直接相连的目的）。所有的IP路由选择只为数据报传输提供下一站路由器的IP地址。

IP路由选择主要完成以下这些功能：

1) 搜索路由表，寻找能与目的IP地址完全匹配的表目 （网络号和主机号都要匹配）。如果找到，则把报文发送给该表目指定的下一站路由器或直接连接的网络接口（取决于标志字段的值）。

2)搜索路由表，寻找能与目的网络号相匹配的表目 。如果找到，则把报文发送给该表目指定的下一站路由器或直接连接的网络接口（取决于标志字段的值）。目的网络上的所有主机都可以通过这个表目来处置。例如，一个以太网上的所有主机都是通过这种表目进行寻径的。这种搜索网络的匹配方法必须考虑可能的子网掩码。

3) 搜索路由表，寻找标为“默认”的表目。如果找到，则把报文发送给该表目指定的下一站路由器。

如果上述步骤都没有成功，那么该数据报就不能被发送。

Attention：

- 数据报中的目的IP地址始终不发生任何变化。
- 每个链路层可能具有不同的数据帧首部，而且链路层的目的地址（如果有的话）始终指的是下一站的链路层地址。

## 3.4 子网寻址

子网编址，是把主机号再分成一个子网号和一个主机号。

由于全0或全1 的主机号都是无效的。

子网对于子网内部的路由器是不透明的。

## 3.5 子网掩码

这个掩码是一个 32 bit的值，其中值为1的比特留给网络号和子网号，为 0的比特留给主机号。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap3/img1.png)

给定IP地址和子网掩码以后，主机就可以确定IP数据报的目的是：

1. 本子网上的主机；
2. 本网络中其他子网中的主机；
3. 其他网络上的主机。

## 3.6 特殊情况的 IP地址

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap3/img2.png)

##  ARP：地址解析协议

当一台主机把以太网数据帧发送到位于同一局域网上的另一台主机时，是根据48bit的以太网地址来确定目的接口的。ARP为IP地址到对应的硬件地址之间提供动态映射。

ARP发送一份称作ARP请求的以太网数据帧给以太网上的每个主，这个过程称为“广播”。ARP请求数据帧中包含目的主机的IP地址。如果你是这个IP地址的拥有者，请回答你的硬件地址。

目的主机的ARP层收到这份广播后，识别出自己的IP地址，于是发送一个ARP应答，这个应答包含IP死Hi和对应的硬件地址。收到ARP应答后，使ARP进行请求- 应答交换的IP数据报现在就可以传送了。

点对点链路不使用ARP。当设置这些链路时（一般在引导过程进行），必须告知内核链路每一端的IP地址。像以太网地址这样的硬件地址并不涉及。

## 4.3 ARP高速缓存

ARP高效运行的关键是由于每个主机上都有一个ARP高速缓存。这个高速缓存存放了最近Internet地址到硬件地址之间的映射记录。

arp 命令用来检查ARP高速缓存：

➜ arp -a

(192.168.100.1) at7c:8:d9:87:e5:85 on en0 ifscope [ethernet]

(192.168.100.255) at(incomplete) on en0 ifscope [ethernet]

## 4.4 ARP分组格式

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap4/img0.png)

目的地址为全1的特殊地址是广播地址。

## 4.6 ARP代理

如果ARP请求是从一个网络的主机发往另一个网络上的主机，那么连接这两个网络的路由器就可以回答该请求，这个过程称作委托 ARP或ARP代理（ProxyARP）。

ARP代理的其他用途：通过两个物理网络之间的路由器可以互相隐藏物理网络。

## 4.7 免费ARP

免费ARP：主机发送ARP查找自己的IP地址。这一般发生在系统引导期间。

免费ARP可以有两个方面的作用：

1) 一个主机可以通过它来确定另一个主机是否设置了相同的IP地址。

2) 如果发送ARP的主机正好改变了硬件地址，那么这个分组就可以使其他主机高速缓存中旧的硬件地址进行相应的更新。

## RARP：逆地址解析协议

无盘系统的RARP实现过程是从接口卡上读取唯一的硬件地址，然后发送一份RARP请求（一帧在网络上广播的数据），请求某个主机响应该无盘系统的IP地址（在RARP应答中）。

## 5.2 RARP的分组格式

RARP分组的格式与ARP分组基本一致。它们之间主要的差别是RARP请求或应答的帧类型代码为 0x8035，而且RARP请求的操作代码为 3，应答操作代码为4。

对应于ARP，RARP请求以广播方式传送，而RARP应答一般是单播(unicast)传送的 。

## 5.4 RARP服务器的设计

RARP服务器的功能由用户进程来提供，原因在于硬件地址和IP地址的映射保存在磁盘文件中，内核一般不读取和分析磁盘文件。

RARP请求是作为一个特殊类型的以太网数据帧发送的。

RARP服务器实现的一个复杂因素是 RARP请求是在硬件层上进行广播的，这意味着它们不经过路由器进行转发。

## ICMP：Internet控制报文协议

ICMP经常被认为是IP层的一个组成部分。它传递差错报文以及其他需要注意的信息。ICMP报文通常被IP层或更高层协议调用。

ICMP报文是在IP数据报内部被传输的。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap6/img0.png)

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap6/img1.png)

检验和字段覆盖整个ICMP报文。

## 6.2 ICMP报文的类型

不同类型由报文中的类型字段和代码字段来共同决定：查询报文 or 差错报文

## 6.3 ICMP地址掩码请求与应答

ICMP地址掩码请求用于无盘系统在引导过程中获取自己的子网掩码。系统广播它的ICMP请求报文。无盘系统获取子网掩码的另一个方法是BOOTP协议

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap6/img2.png)

ICMP报文中的标识符和序列号字段由发送端任意选择设定，这些值在应答中将被返回。这样，发送端就可以把应答与请求进行匹配

## 6.4 ICMP时间戳请求与应答

ICMP时间戳请求允许系统向另一个系统查询当前的时间。返回的建议值是自午夜开始计算的毫秒数。这种ICMP报文的好书是提供了毫秒级的分辨率，但调用者必须通过其方法知道当前的日期。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap6/img3.png)

几乎所有的主机都把接收时间戳和发送时间戳设置成相同的值。我们仍然可以根据接收到应答时的时间值减去发送请求时的时间值算出往返时间（rtt）。

## 6.5 ICMP端口不可达差错

UDP的规则之一是，如果收到一份UDP数据报而目的端口与某个正在使用的进程不相符，那么UDP返回一个ICMP不可达报文。可以用TFTP来强制生成一个端口不可达报文。

ICMP报文是在主机之间交换的，而不用目的端口号，而每个20字节的UDP数据报。则是从一个特定端口。发送到另一个特定端口。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap6/img4.png)

ICMP差错报文必须包括生成该差错报文的数据报IP首部（包含任何选项），还必须至少包括跟在该 IP首部后面的前8个字节。

一个重要的事实是包含在UDP首部中的内容是源端口号和目的端口号。就是由于目的端口号才导致产生了 ICMP端口不可达的差错报文。接收 ICMP的系统可以根据源端口号来把差错报文与某个特定的用户进程相关联。

导致差错的数据报中的IP首部要被送回的原因是因为IP首部中包含了协议字段，使得 ICMP可以知道如何解释后面的 8个字节。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap6/img5.png)

## Ping程序

ping程序，目的是为了测试另一台主机是否可达。该程序发送一份ICMP回显请求报文给主机，并等待返回ICMP回显应答，不用经过传输层TCP/UDP。

一般来说，如果不能Ping到某台主机，那就不能telnet活ftp到它。但是一台主机的可泰兴不只取决于IP层是否可达，还取决于使用何种协议和端口号。Ping的结果可能显示某台主机不可达，但可以用Telnet远程登录该主机的25号端口。

## 7.2 Ping程序

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap7/img0.png)

UNIX在实现ping时，把ICMP报文中的标识符设置成发送进程的PID。这样就可以同时运行多个ping程序。

ping程序通过在ICMP报文数据中存放发送请求的时间值来计算往返时间。当应答返回时，用当前时间减去存放在ICMP报文中的时间值，即是往返时间。

## 7.3 IP记录路由选项

大多数不同版本的ping程序都提供-R选项，以提供记录路由的功能。

它使得ping程序在发送出去的IP数据报中设置IP RR选项（该IP数据报包含ICMP回显请求报文）。这样， 每个处理该数据报的路由器都把它的 IP地址放入选项字段中。当数据报到达目的端时，IP地址清单应该复制到ICMP回显应答中，这样返回途中所经过的路由器地址也被加入清单中。当ping程序收到回显应答时，它就打印出这份IP地址清单。

IP首部有它的长度限制，所以只能存放9个IP地址。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap7/img1.png)

## 7.4 IP时间戳选项

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap7/img2.png)

## Traceroute程序

traceroute程序可以让我们看到IP数据报从一台主机传到另一台主机所经过的路由。traceroute程序还可以让我们使用IP源路由选项。

## 8.2 Traceroute程序的操作

为什么不使用IP记录路由选项（RR）而另外开发一个新的traceroute？

1. 原先并不是所有的路由器都支持记录路由选项
2. 记录路由一般是单向的选项
3. IP首部中留给选项的空间有限，不能存放当前大多数的路径

traceroute程序使用ICMP报文和IP首部中的TTL字段。TTL字段是由发送端初始设置一个8bit字段。推荐的初始值由分配数字RFC指定，当前值为64。

每个处理数据报的路由器都需要把TTL的值减1 或减去数据报在路由器中停留的秒数。由于大多数的路由器转发数据报的时延都小于1秒钟，因此TTL最终成为一个跳站的计数器，所经过的每个路由器都将其值减1。

TTL字段的目的是防止数据报在选路时无休止地在网络中流动。当路由器收到一个IP数据报，TTL是0或1，丢弃该数据报，并给信源发送一份ICMP超时信息。Traceroute的关键在于包含这份ICMP信息的IP报文的信源地址是该路由器的IP地址。

所以Traceroute的操作过程是：先发送一份TTL字段为1的IP数据报给目的主机，得到第一个路由器的地址；然后发送一个TTL字段为2的IP数据报，以此类推，直到达到目的主机。

## 8.5 IP源站选路选项

源站选路(source routing) 的思想是由发送者指定路由。它可以采用以下两种形式：

1. 严格的源路由选择。发送端指明IP数据报所必须采用的确切路由。如果一个路由器发现源路由所指定的下一个路由器不在其直接连接的网络上,那么它就返回一个“源站路由失败”的ICMP差错报文。
2. 宽松的源站选路。发送端指明了一个数据报经过的IP地址清单，但是数据报在清单上指明的任意两个地址之间可以通过其他路由器。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap8/img0.png)

源站路由选项的实际称呼为“源站及记录路由”（对于宽松的源站选路和严格的源站选路，分别用 LSRR和SSRR 表示），这是因为在数据报沿路由发送过程中，对 IP地址清单进行了更新。下面是其运行过程：

1. 发送主机从应用程序接收源站路由清单，将第1表项去掉（它是数据报的最终目的地址），将剩余的项移到1个项中，并将原来的目的地址作为清单的最后一项。指针仍然指向清单的第 1项（即，指针的值为4）。
2. 每个处理数据报的路由器检查其是否为数据报的最终地址。如果不是，则正常转发数据报（在这种情况下，必须指明宽松源站选路，否则就不能接收到该数据报）。
3. 如果该路由器是最终目的，且指针不大于路径的长度，那么 ( 1)由ptr 所指定的清单中的下一个地址就是数据报的最终目的地址； (2)由外出接口(outgoing interface) 相对应的 I P地址取代刚才使用的源地址； (3)指针加4 。

## IP选路

![9. IP选路 - 图1](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap9/img0.png)

## 9.2 选路的原理

IP搜索路由表的几个步骤：

1) 搜索匹配的主机地址；

2) 搜索匹配的网络地址；

3) 搜索默认表项

IP层进行的选路实际上是一种选路机制，它搜索路由表并决定向哪个网络接口发送分组。这区别于选路策略，它只是一组决定把哪些路由放入路由表的规则。IP执行选路机制，而路由守护程序则一般提供选路策略。

每当初始化一个接口时（通常用ifconfig设置接口地址），就为接口自动创建一个直接路由。到达不直接相连的主机或网络必须以某种方式添加到路由表中，一个常用方式是：

1. 在系统引导时显式地在初始化文件中运行route命令
2. 运行路由守护程序。或者用较新的路由器发现协议

如果路由表中没有默认项，又没有找到匹配项，结果取决于该IP数据报是由主机产生还是被转发的。如果是本机产生的，那么久给发送该数据报的应用程序返回一个差错，或者是“主机不可达差错”或者“网络不可达差错”。如果是被转发的数据报，那么就给原始发送端发送一份ICMP主机不可达的差错报文。

## 9.3 ICMP主机与网络不可达差错

当路由器收到一份IP数据报但又不能转发时，就要发送一份ICMP“主机不可达”差错报文。

## 9.4 转发或不转发

一般都假定主机不转发IP数据报，除非对它们进行特殊配置而作为路由器使用。

大多数伯克利派生出来的系统都有一个内核变量ipforwarding，或其他类似的名字。一些系统（如BSD/386和SVR4）只有在该变量值不为0的情况下才转发数据报。

## 9.5 ICMP重定向差错

当IP数据报应该被发送到另一个路由器时，收到数据报的路由器就要发送ICMP重定向差错报文给IP数据报的发送端。

重定向一般用来让具有很少选路信息的主机逐渐建立更完善的路由表。主机启动时路由表中可以只有一个默认表项。一旦默认路由发生差错，默认路由器将通知它进行重定向，并允许主机对路由表作相应的改动。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap9/img1.png)

重定向报文有许多规则：

1. 重定向报文只能由路由器生成，不能由主机生成
2. 重定向报文是为主机而不是路由器使用的
3. 路由器发应该发送的是对主机的重定向，而不是对网络的重定向。因为子网的存在使得难于准确指明何时应发送对网络的重定向。

## 9.6 ICMP路由器发现报文

在本章前面已提到过一种初始化路由表的方法，即在配置文件中指定静态路由（Route命令）。这种方法经常用来设置默认路由。另一种新的方法是利用ICMP路由器通告和请求报文。

主机在引导后会广播/多播一份路由器请求报文。另外，路由器会定期广播/多播传送他们的路由器通告报文，允许每个正在监听的主机更新它们的路由表。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap9/img2.png)

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap9/img3.png)

## 路由器操作

当路由器启动时，它定期（一般不是定义，随机传送的，减少冲突）在所有广播或多播传送接口上发送通告报文。路由器还要监听来自主机的请求报文，并发送路由器通告报文以响应这些请求报文。

## 主机操作

主机在引导期间一般发送三份路由器请求报文，每三秒钟发送一次。一旦接收到一个有效的通告报文，就停止发送请求报文。

主机也监听来自相邻路由器的请求报文。这些通告报文可以改变主机的默认路由器。另外，如果没有接收到来自当前默认路由器的通告报文，那么默认路由器会超时。

路由器发现报文一般由用户进程（守护程序）创建和处理。

## 动态选路协议

## 静态选路

在配置接口时，以默认方式生成路由表项（对于直接连接的接口），并通过route命令增加表项（通常从系统自引导程序文件），或是通过ICMP重定向生成表项（通常是在默认方式出错的情况下）。

当相邻路由器之间进行通信，以告知对方每个路由器当前所连接的网络，这就出现了动态选路。

## 10.2 动态选路

路由器之间必须采用选路协议进行通信，路由器上有个进程为路由守护程序，它运行选路协议，与相邻路由进行通信。

动态选路并不改变内核在IP层的选路方式。这种选路方式称为选路机制（routingmechanism）。内核搜索路由表，查找主机路由、网络路由以及默认路由的方式并没有改变。仅仅是放置到路由表中的信息改变了——当路由随时间变化时，路由是由路由守护程序动态地增加或删除，而不是来自于自引导程序文件中的route命令。

每个自治系统可以选择该自治系统中各个路由器之间的选路协议。这种协议我们称之为内部网关协议IGP(InteriorGateway Protocol），最常用的IGP是选路信息协议RIP。一种新的IGP是开放最短路径优先OSPF

外部网关协议EGP(Exterier GatewayProtocol）或域内选路协议的分隔选路协议用于不同自治系统之间的路由器。

## 10.3 UNIX选路守护程序

UNIX上运行名为routed的路由守护进程，它只是用RIP进行通信。

另一个程序是gated。IGP和EGP都支持它。大多数系统都可以运行routed，除非需要支持gated所支持的其他协议。

## 10.4 RIP：选路信息协议

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap10/img0.png)

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap10/img1.png)

让我们来看一下采用RIP协议的routed程序正常运行的结果。RIP常用的UDP端口号是520。

1. 初始化：在启动一个路由守护程序时，它先判断启动了哪些接口，并在每个接口上发送一个请求报文，要求其他路由器发送完整路由表。
2. 接收到请求。如果这个请求是刚才提到的特殊请求，那么路由器就将完整的路由表发送给请求者。否则，就处理请求中的每一个表项：如果有连接到指明地址的路由，则将度量设置成我们的值，否则将度量置为16（度量为16是一种称为“无穷大”的特殊值，它意味着没有到达目的的路由）。然后发回响应。
3. 接收到响应。使响应生效，可能会更新路由表。可能会增加新表项，对已有的表项进行修改，或是将已有表项删除。
4. 定期选路更新。每过30秒，所有或部分路由器会将其完整路由表发送给相邻路由器。发送路由表可以是广播形式的（如在以太网上），或是发送给点对点链路的其他终点的。
5. 触发更新。每当一条路由的度量发生变化时，就对它进行更新。不需要发送完整路由表，而只需要发送那些发生变化的表项。

每条路由都有与之相关的定时器。如果运行RIP的系统发现一条路由在 3分钟内未更新，就将该路由的度量设置成无穷大（16），并标注为删除。这意味着已经在 6个30秒更新时间里没收到通告该路由的路由器的更新了。再过60秒，将从本地路由表中删除该路由，以保证该路由的失效已被传播开。

RIP所使用的度量是以跳(hop)计算的。

## 10.6 OSPF：开放最短路径优先

与采用距离向量的RIP协议不同的是，OSPF是一个链路状态协议。距离向量的意思是，RIP发送的报文包含一个距离向量（跳数）。每个路由器都根据它所接收到邻站的这些距离向量来更新自己的路由表。

在一个链路状态协议中，路由器并不与其邻站交换距离信息。它采用的是每个路由器主动地测试与其邻站相连链路的状态，将这些信息发送给它的其他邻站，而邻站将这些信息在自治系统中传播出去。每个路由器接收这些链路状态信息，并建立起完整的路由表。

OSPF与 RIP（以及其他选路协议）的不同点在于， OSPF直接使用IP。也就是说，它并不使用UDP或TCP。对于ip首部的protocol字段，OSPF有其自己的值。

## 10.7 BGP：边界网关协议

BGP是一种不同自治系统的路由器之间进行通信的外部网关协议。

BGP系统与其他 BGP系统之间交换网络可到达信息。这些信息包括数据到达这些网络所必须经过的自治系统AS中的所有路径。这些信息足以构造一幅自治系统连接图。然后，可以根据连接图删除选路环，制订选路策略。

BGP允许使用基于策略的选路。由自治系统管理员制订策略，并通过配置文件将策略指定给 BGP。与RIP和OSPF不同的是，BGP采用TCP作为其传输层协议。两个运行BGP的系统之间建立一条TCP连接。

BGP是一个距离向量协议，但是与（通告到目的地址跳数的） RIP不同的是，BGP 列举了到每个目的地址的路由。

## 10.8 CIDR：无类型域间选路

无类型域间选路（CIDR）是一个防止Internet路由表膨胀的方法，它也称为超网。

CIDR的基本观点是采用一种分配多个ip地址的方式，使其能够将路由表中的许多表项总和（summarization）成更少的数目。

“无类型”的意思是现在的选路决策是基于整个 32 bit IP地址的掩码操作，而不管其ip地址是A类、B类或是C类，都没有什么区别。

## UDP：用户数据报协议

UDP是一个简单的面向数据报的运输层协议

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap11/img0.png)

UDP不提供可靠性：它把应用程序传给IP层的数据发送出去，但是并不保证它们能到达目的地。

## 11.2 UDP首部

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap11/img1.png)

端口号表示发送进程和接收进程。UDP长度字段指的是UDP首部和UDP数据的字节长度。

## 11.3 UDP检验和

UDP检验和覆盖UDP首部和UDP数据。回想IP首部的检验和，它只覆盖IP的首部。

UDP的检验和是可选的，而TCP的检验和是必需的。

UDP检验和的基本计算方法与IP首部检验和计算方法相类似（16bit字的二进制反码和），但是它们之间存在不同的地方。首先，UDP数据报的长度可以为奇数字节，但是检验和算法是把若干个16bit字相加。解决方法是必要时在最后增加填充字节 0，这只是为了检验和的计算（也就是说，可能增加的填充字节不被传送）。

其次，UDP数据报和TCP段都包含一个12字节长的伪首部，它是为了计算检验和而设置的。伪首部包含 IP首部一些字段。其目的是让 UDP两次检查数据是否已经正确到达目的地。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap11/img2.png)

## 11.5 IP分片

把一份IP数据报分片以后，只有到达目的地才进行重新组装。重新组装由目的端的IP层来完成，其目的是使分片和重新组装过程对运输层（TCP和UDP）是透明的，IP首部中包含的数据为分片和重新组装提供了足够的信息。

对于发送端发送的每份IP数据报来说，其标识字段都包含一个唯一值。该值在数据报分片时被复制到每个片中。标志字段用其中一个比特来表示“更多的片”。除了最后一片外，其他每个组成数据报的片都要把该比特置 1。片偏移字段指的是该片偏移原始数据报开始处的位置。

另外，当数据报被分片后，每个片的总长度值要改为该片的长度值。最后，标志字段中有一个比特称作“不分片”位。如果将这一比特置 1，IP将不对数据报进行分片。相反把数据报丢弃并发送一个ICMP差错报文给起始端。

当IP数据报分片后，每一片都成为一个分组，有自己的IP首部，并在选择路由器时与其他分组独立。固有可能在到达目的端时失序。

一片数据的丢失也要重传整个数据报。因为对数据报分片的是中间路由器，而不是起始端系统，后者根本不知道数据报是如何分片的。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap11/img3.png)

PS.任何运输层的首部只出现在第一片数据中。

## 11.6 ICMP不可达差错（需要分片）

发送ICMP不可达差错的另一种情况是，当路由器收到一份需要分片的数据报，而在IP首部又设置了不分片（DF）的标志比特。如果某个程序需要判断到达目的端的路途中最小MTU是多少 — 称作路径MTU发现机制，那么这个差错就可以被该程序使用。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap11/img4.png)

## 11.7 用Traceroute 确定路径MTU

修改traceroute程序确定路径MTU：发送分组，设置“不分片”标志比特。发送的第一个分组长度正好与出口MTU相等，每次收到ICMP“不能分片”差错是就减少分组的长度。

## 11.8 采用UDP的路径MTU发现

UDP应用可以关闭或开启该路径MTU发现，只要修改ip_path_mtu_discovery参数即可。

## 11.10 最大 UDP数据报长度

理论上，IP数据报的最大长度是65535字节，这是由IP首部16比特总长度字段所限制的。去除2 0字节的IP首部和8个字节的 UDP首部，UDP数据报中用户数据的最长长度为 65507字节。但是，大多数实现所提供的长度比这个最大值小。

我们会遇到两个限制因素：

1. 应用程序收到其程序接口的限制。比如socket API就可以设置接收和发送缓存的长度
2. 来自TCP/IP的内核实现。

## 11.11 ICMP源站抑制差错

当一个系统（路由器或主机）接收数据报的速度比其处理速度快时，可能产生这个差错。注意限定词“可能”。即使一个系统已经没有缓存并丢弃数据报，也不要求它一定要发送源站抑制报文。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap11/img5.png)

## 广播和多播

广播是将数据报发送到网络中的所有主机（通常是本地相连的网络），而多播是将数据报发送到网络的一个主机组。

广播和多播仅应用于UDP。

使用广播的问题在于它增加了对广播数据不感兴趣主机的处理负荷。多播的出现减少了对应用不感兴趣主机的处理负荷。使用多播，主机可加入一个或多个多播组。

## 12.2 广播

四种广播地址

1. 受限的广播， 255.255.255.255，该地址用于主机配置过程中IP数据报的目的地址。在任何情况下，路由器都不转发目的地址为受限的广播地址的数据报，这样的数据报仅出现在本地网络中。
2. 指向网络的广播，指向网络的广播地址是主机号为全1的地址。A类网络广播的士为netid.255.255.255。一个路由器必须转发指向网络的广播，但它也有一个不转发的选择。
3. 指向子网的广播，地址为主机号为全 1且有特定子网号的地址。
4. 指向所有子网的广播，需要了解目的网络的子网掩码，以便与指向网络的广播地址区分开。指向所有子网的广播地址的子网号及主机号为全1。

广播是怎样传送的？路由器及主机又如何处理广播？这些问题有赖于广播的类型、应用的类型、TCP/IP实现以及有关路由器的配置。

## 12.4 多播

多播组地址包括为1110的最高4bit和多播组号。它们通常可表示为点分十进制数，范围从224.0.0.0到239.255.255.255 。一个主机组可以跨越多个网络。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap12/img0.png)

通过将其低位 23bit映射到相应以太网地址中便可实现多播组地址到以太网地址的转换。由于地址映射是不唯一的，因此需要其他的协议实现额外的数据报过滤。

## ICMP：Internet组管理协议

支持主机和路由器进行多播的Internet组管理协议（IGMP）。它让一个物理网络上的所有系统知道主机当前所在的多播组。

IGMP也被当作IP层的一部分。IGMP报文通过IP数据报进行传输。IGMP有固定的报文长度，没有可选数据。

## IGMP报文

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap13/img0.png)

## IGMP协议

多播的基础就是一个进程的概念，该进程在一个主机的给定接口上加入了一个多播组。在一个给定接口上的多播组中的成员是动态的 ——它随时因进程加入和离开多播组而变化。

多播路由器使用IGMP报文来记录与该路由器相连网络中组成员的变化情况。使用规则如下：

1) 当第一个进程加入一个组时，主机就发送一个IGMP报告。如果一个主机的多个进程加入同一组，只发送一个IGMP报告。这个报告被发送到进程加入组所在的同一接口上。

2) 进程离开一个组时，主机不发送IGMP报告，即便是组中的最后一个进程离开。主机知道在确定的组中已不再有组成员后，在随后收到的IGMP查询中就不再发送报告报文。

3) 多播路由器定时发送 IGMP查询来了解是否还有任何主机包含有属于多播组的进程。多播路由器必须向每个接口发送一个 IGMP查询。因为路由器希望主机对它加入的每个多播组均发回一个报告，因此 IGMP查询报文中的组地址被设置为 0。

4) 主机通过发送 IGMP报告来响应一个IGMP查询，对每个至少还包含一个进程的组均要发回 IGMP报告。

使用这些查询和报告报文，多播路由器对每个接口保持一个表，表中记录接口上至少还包含一个主机的多播组。当路由器收到要转发的多播数据报时，它只将该数据报转发到（使用相应的多播链路层地址）还拥有属于那个组主机的接口上。

## DNS：域名系统

DNS是一种用于TCP/IP应用程序的分布式数据库，它提供主机名字和IP地址之间的转换及有关电子邮件的选路信息。

## DNS基础

没有哪个机构来管理域名树中的每个标识，相反，只有一个机构，即网络信息中心NIC负责分配顶级域和委派其他指定地区域的授权机构。

一个名字服务器负责一个或多个区域。一个区域的管理者必须为该区域提供一个主名字。服务器和至少一个辅助名字服务器。主、辅名字服务器必须是独立和冗余的，以便当某个名字服务器发生故障时不会影响该区域的名字服务。主、辅名字服务器的主要区别在于主名字服务器从磁盘文件中调入该区域的所有信息，而辅名字服务器则从主服务器调入所有信息。

## DNS的报文格式

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap14/img0.png)

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap14/img1.png)

DNS查询报文中的问题部分

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap14/img2.png)

DNS响应报文中的资源记录部分

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap14/img3.png)

## 指针查询

指针查询方式，即给定一个IP地址，返回与该地址对应的域名。

## 高速缓存

为了减少Internet上DNS的通信量，所有的名字服务器均使用高速缓存。在标准的Unix实现中，高速缓存是由名字服务器而不是由名字解析器维护的。

## 用UDP还是用 TCP

DNS名字服务器使用的熟知端口号无论对UDP还是TCP都是53。这意味着DNS均支持UDP和TCP访问。

## 小结

应用程序通过名字解析器将一个主机名转换为一个IP地址，也可将一个IP地址转换为与之对应的主机名。名字解析器将向一个本地名字服务器发出查询请求，这个名字服务器可能通过某个根名字服务器或其他名字服务器来完成这个查询。

所有的DNS查询和响应都有相同的报文格式。这个报文格式中包含查询请求和可能的回答资源记录、授权资源记录和附加资源记录。通过许多例子了解了名字解析器的配置文件以及 DNS的优化措施：指向域名的指针（减少报文的长度）、查询结果的高速缓存、 in-addr.arpa域（查找IP 地址对应的域名）以及返回的附加资源记录（避免主机重发同一查询请求）。

## TFTP：简单文件传送协议

TFTP将使用UDP。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap15/img0.png)

TFTP使用不可靠的UDP，TFTP就必须处理分组丢失和分组重复。分组丢失可通过发送方的超时与重传机制解决。

TFTP协议没有提供安全特性。大多数执行指望TFTP服务器的系统管理员来限制客户的访问，只允许它们访问引导所必须的文件。

TFTP使用停止等待协议，数据发送方在发送下一个数据块之前需要等待接受对已发送数据的确认。

## BOOTP：引导程序协议

BOOTP使用UDP，且通常需与TFTP协同工作。

## BOOTP 的分组格式

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap16/img0.png)

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap16/img1.png)

BOOTP有两个熟知端口：BOOTP服务器为67，BOOTP客户为68。这意味着BOOTP客户不会选择未用的临时端口，而只用端口68。选择两个端口而不是仅选择一个端口为BOOTP服务器用的原因是：服务器的应答可以进行广播（但通常是不用广播的）。

BOOTP服务器比ARP服务器更易于实现，因为BOOTP请求和应答是在UDP数据报中，而不是特殊的数据链路层帧。一个路由器还能作为真正 BOOTP服务器的代理，向位于不同网络的真正BOOTP服务器转发客户的BOOTP请求。RARP是链路层广播，不会被路由器转发。

## TCP：传输控制协议

TCP提供一种面向连接的、可靠的字节流服务。

TCP通过下列方式来提供可靠性。

1. 应用数据被分割成TCP认为最适合发送的数据块。这和UDP完全不同，应用程序产生的数据报长度将保持不变。
2. 超时重传
3. 需要确认
4. 保持首部和数据的检验和
5. 数据后重新排序
6. 丢弃重复
7. 流量控制

TCP不在字节流中插入记录标识符。我们将这称为字节流服务。 TCP对字节流的内容不作任何解释。

## TCP首部

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap17/img0.png)

TCP首部的数据格式。如果不计任选字段，它通常是20个字节。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap17/img1.png)

每个TCP段都包含源端和目的端的端口号，用于寻找发端和收端应用进程。这两个值加上IP首部中的源端IP地址和目的端IP地址唯一确定一个TCP连接。有时，一个IP地址和一个端口号也称为一个插口（socket）。

每个传输的字节都被计数，确认序号包含发送确认的一端所期望收到的下一个序号。

TCP为应用层提供全双工服务。这意味数据能在两个方向上独立地进行传输。

检验和覆盖了整个的TCP报文段：TCP首部和TCP数据。这是一个强制性的字段，一定是由发端计算和存储，并由收端进行验证。 TCP检验和的计算和UDP检验和的计算相似，使用一个伪首部。

许多流行的应用程序如Telnet、 Rlogin、FTP和SMTP都使用TCP。

## TCP连接的建立与终止

建立一个连接需要三次握手，而终止一个连接要经过4次握手。

为了建立一条TCP连接：

1. 请求端（通常称为客户）发送一个SYN段指明客户打算连接的服务器的端口，以及初始序号。这个 SYN段为报文段1 。
2. 服务器发回包含服务器的初始序号的SYN报文段（报文段2）作为应答。同时，将确认序号设置为客户的ISN加1 以对客户的 SYN报文段进行确认。一个SYN将占用一个序号。
3. 客户必须将确认序号设置为服务器的ISN加1 以对服务器的SYN报文段进行确认（报文段 3）。

![img](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap18/img0.png)

![img](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap18/img1.png)

## 最大报文段长度

最大报文段长度MSS表示TCP传往另一端的最大块数据的长度。当一个连接建立时，连接的双方都要通告各自的MSS。

MSS让主机限制另一端发送数据报的长度。加上主机也能控制它发送数据报的长度，这将使以较小MTU连接到一个网络上的主机避免分段。

## TCP的半关闭

TCP提供了连接的一端在结束它的发送后还能接收来自另一端数据的能力。

![img](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap18/img2.png)

## TCP的状态变迁图

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap18/img3.png)

## 复位报文段

TCP首部中的RST比特是用于“复位”的。一般说来，无论何时一个报文。段发往基准的连接（ referenced connection）出现错误，TCP都会发出一个复位报文段（这里提到的“基准的连接”是指由目的 I P地址和目的端口号以及源 I P地址和源端口号指明的连接）。

产生复位的一种常见情况是当连接请求到达时，目的端口没有进程正在听。对于 UDP，我们在6 . 5 节看到这种情况，当一个数据报到达目的端口时，该端口没在使用，它将产生一个 I C M P端口不可达的信息。而 TCP则使用复位。

异常终止一个连接，或者检测半打开连接都需要发送一个复位报文段。

## 同时打开

两个应用程序同时彼此执行主动打开的情况是可能的。每一方必须发送一个SYN，且这些SYN 必须传递给对方。这需要每一方使用一个对方熟知的端口作为本地端口。这又称为同时打开。

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap18/img4.png)

## 同时关闭

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap18/img5.png)

## TCP选项

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap18/img6.png)

## TCP的交互数据流

交互数据总是以小于最大报文段长度的分组发送。

## 经受延时的确认

对于这些小的报文段，接收方使用经受时延的确认方法来判断确认是否可被推迟发送，以便与回送数据一起发送。这样通常会减少报文段的数目，尤其是对于需要回显用户输入字符的Rlogin会话。

TCP将以最大 200 ms 的时延等待是否有数据一起发送。

## Nagle算法

在较慢的广域网环境中，通常使用 Nagle算法来减少这些小报文段的数目。这个算法限制发送者任何时候只能有一个发送的小报文段未被确认。

该算法要求一个TCP连接上最多只能有一个未被确认的未完成的小分组，在该分组的确认到达之前不能发送其他的小分组。相反， TCP收集这些少量的分组，并在确认到来时以一个分组的方式发出去。

## TCP的成块数据流

TCP所使用的被称为滑动窗口协议的另一种形式的流量控制方法。该协议允许发送方在停止并等待确认前可以连续发送多个分组。由于发送方不必每发一个分组就停下来等待确认，因此该协议可以加速数据的传输。

## 滑动窗口

![graphic](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap20/img0.png)

发送方计算它的可用窗口，该窗口表明多少数据可以立即被发送。

我们使用三个术语来描述窗口左右边沿的运动：

1. 称窗口左边沿向右边沿靠近为窗口合拢。这种现象发生在数据被发送和确认时。
2. 当窗口右边沿向右移动时将允许发送更多的数据，我们称之为窗口张开。这种现象发生在另一端的接收进程读取已经确认的数据并释放了 TCP的接收缓存时。
3. 当右边沿向左移动时，我们称之为窗口收缩。

## 窗口大小

由接收方提供的窗口的大小通常可以由接收进程控制，这将影响TCP的性能。

## PUSH标志

发送方使用PUSH标志通知接收方将所收到的数据全部提交给接收进程。这里的数据包括与PUSH一起传送的数据以及接收方 TCP已经为接收进程收到的其他数据。

## 慢启动

TCP需要支持一种被称为“慢启动 (slowstart)”的算法。该算法通过观察到新分组进入网络的速率应该与另一端返回确认的速率相同而进行工作。

慢启动为发送方的TCP增加了另一个窗口：拥塞窗口 (congestion window)，记为cwnd 。

发送方取拥塞窗口与通告窗口中的最小值作为发送上限。拥塞窗口是发送方使用的流量控制，而通告窗口则是接收方使用的流量控制

## 紧急方式

TCP提供了“紧急方式 ( urgent mode) ”，它使一端可以告诉另一端有些具有某种方式的“紧急数据”已经放置在普通的数据流中。另一端被通知这个紧急数据已被放置在普通数据流中，由接收方决定如何处理。

只要从接收方当前读取位置到紧急数据指针之间有数据存在，就认为应用程序处于“紧急方式”。

## TCP的超时与重传

对每个连接，TCP管理4个不同的定时器：

1) 重传定时器使用于当希望收到另一端的确认。
2) 坚持(persist)定时器使窗口大小信息保持不断流动，即使另一端关闭了其接收窗口。
3) 保活( keepalive )定时器可检测到一个空闲连接的另一端何时崩溃或重启。这个定时器。
4) 2MSL定时器测量一个连接处于TIME_WAIT状态的时间。

## 往返时间测量

首先TCP必须测量在发送一个带有特别序号的字节和接收到包含该字节的确认之间的RT T。最初的TCP规范使TCP使用低通过滤器来更新一个被平滑的RTT估计器：

![21. TCP的超时与重传 - 图1](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap21/img0.png)

**Karn算法**：当一个超时和重传发生时，在重传数据的确认最后到达之前，不能更新RTT估计器，因为我们并不知道ACK对应哪次传输。

## 拥塞避免算法

拥塞避免算法和慢启动算法需要对每个连接维持两个变量：一个拥塞窗口cwnd和一个慢启动门限ssthresh。这样得到的算法的工作过程如下：

1) 对一个给定的连接，初始化cwnd为1个报文段，ssthresh为65535个字节。
2) TCP输出例程的输出不能超过 cwnd和接收方通告窗口的大小。拥塞避免是发送方使用的流量控制，而通告窗口则是接收方进行的流量控制。前者是发送方感受到的网络拥塞的估计，而后者则与接收方在该连接上的可用缓存大小有关。
3) 当拥塞发生时（超时或收到重复确认），ssthresh被设置为当前窗口大小的一半（cwnd和接收方通告窗口大小的最小值，但最少为 2个报文段）。此外，如果是超时引起了拥塞，则cwnd被设置为1个报文段（这就是慢启动）。
4) 当新的数据被对方确认时，就增加 cwnd，但增加的方法依赖于我们是否正在进行慢启动或拥塞避免。如果 cwnd小于或等于ssthresh，则正在进行慢启动，否则正在进行拥塞避免。慢启动一直持续到我们回到当拥塞发生时所处位置的半时候才停止（因为我们记录了在步骤2中给我们制造麻烦的窗口大小的一半），然后转为执行拥塞避免。

慢启动算法初始设置 cwnd为1个报文段，此后每收到一个确认就加 1。那样，这会使窗口按指数方式增长：发送 1个报文段，然后是2个，接着是4个……

拥塞避免算法要求每次收到一个确认时将 cwnd增加1 /cwnd。与慢启动的指数增加比起来，这是一种加性增长(additive increase)。我们希望在一个往返时间内最多为 cwnd增加1个报文段（不管在这个RT T中收到了多少个ACK），然而慢启动将根据这个往返时间中所收到的确认的个数增加cwnd。

![21. TCP的超时与重传 - 图2](https://static.sitestack.cn/projects/lutzchuck-tcpip-note/img/chap21/img1.png)

## 快速重传与快速恢复算法

这个算法通常按如下过程进行实现：

1) 当收到第3个重复的ACK时，将ssthresh设置为当前拥塞窗口cwnd的一半。重传丢失的报文段。设置cwnd为ssthresh加上3倍的报文段大小。
2) 每次收到另一个重复的 ACK时，cwnd增加1个报文段大小并发送 1个分组（如果新的cwnd允许发送）。
3) 当下一个确认新数据的ACK到达时，设置cwnd为ssthresh（在第1步中设置的值）。这个ACK应该是在进行重传后的一个往返时间内对步骤 1中重传的确认。另外，这个 ACK也应该是对丢失的分组和收到的第1个重复的ACK之间的所有中间报文段的确认。这一步采用的是拥塞避免，因为当分组丢失时我们将当前的速率减半。

## ICMP的差错

TCP能够遇到的最常见的ICMP差错就是源站抑制、主机不可达和网络不可达。当前基于伯克利的实现对这些错误的处理是：

1. 一个接收到的源站抑制引起拥塞窗口cwnd被置为1个报文段大小来发起慢启动，但是慢启动门限ssthresh没有变化，所以窗口将打开直至它或者开放了所有的通路（受窗口大小和往返时间的限制）或者发生了拥塞。
2. 一个接收到的主机不可达或网络不可达实际上都被忽略，因为这两个差错都被认为是短暂现象。

## TCP的坚持定时器

如果一个确认丢失了，则双方就有可能因为等待对方而使连接终止：接收方等待接收数据（因为它已经向发送方通告了一个非 0的窗口），而发送方在等待允许它继续发送数据的窗口更新。为防止这种死锁情况的发生，发送方使用一个坚持定时器 (persist timer)来周期性地向接收方查询，以便发现窗口是否已增大。这些从发送方发出的报文段称为窗口探查。

## 糊涂窗口综合症

接收方可以通告一个小的窗口（而不是一直等到有大的窗口时才通告），而发送方也可以发送少量的数据（而不是等待其他的数据以便发送一个大的报文段）。可以在任何一端采取措施避免出现糊涂窗口综合症的现象。
1) 接收方不通告小窗口。通常的算法是接收方不通告一个比当前窗口大的窗口（可以为0），除非窗口可以增加一个报文段大小（也就是将要接收的 MSS）或者可以增加接收方缓存空间的一半，不论实际有多少。
2) 发送方避免出现糊涂窗口综合症的措施是只有以下条件之一满足时才发送数据：

> (a) 可以发送一个满长度的报文段；
> (b) 可以发送至少是接收方通告窗口大小一半的报文段；
> (c) 可以发送任何数据并且不希望接收ACK（也就是说，我们没有还未被确认的数据）或者该连接上不能使用Nagle算法。

## TCP的保活定时器

如果TCP连接的双方都没有向对方发送数据，则在两个TCP模块之间不交换任何信息。

如果一个给定的连接在两个小时之内没有任何动作，则服务器就向客户发送一个探查报文段。。客户主机必须处于以下 4个状态之一。

1) 客户主机依然正常运行，并从服务器可达。客户的 TCP响应正常，而服务器也知道对方是正常工作的。服务器在两小时以后将保活定时器复位。如果在两个小时定时器到时间之前有应用程序的通信量通过此连接，则定时器在交换数据后的未来2小时再复位。
2) 客户主机已经崩溃，并且关闭或者正在重新启动。在任何一种情况下，客户的TCP都没有响应。服务器将不能够收到对探查的响应，并在75秒后超时。服务器总共发送 10个这样的探查，每个间隔75秒。如果服务器没有收到一个响应，它就认为客户主机已经关闭并终止连接。
3) 客户主机崩溃并已经重新启动。这时服务器将收到一个对其保活探查的响应，但是这个响应是一个复位，使得服务器终止这个连接。
4) 客户主机正常运行，但是从服务器不可达。这与状态 2相同，因为TCP不能够区分状态4与状态2之间的区别，它所能发现的就是没有收到探查的响应。
在第1种情况下，服务器的应用程序没有感觉到保活探查的发生。 TCP层负责一切。这个过程对应用程序都是透明的，直至第 2、3或4种情况发生。在这三种情况下，服务器应用程序将收到来自它的TCP的差错报告