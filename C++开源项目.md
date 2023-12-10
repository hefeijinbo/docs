   #STL：C++标准模板库，呵呵，它也是开源的嘛。

   boost：C++准标准库，它是强大地，江湖称之“千锤百炼”。

   iconv /iconvpp ： (C形式的编码转换函数库，

   C++的XML相关库不少，但是大部分其实都是C库，使用起来自然不那么轻便。其中基于DOM的有TinyXml，基于SAX的当然是Xerces。前者小巧快捷，便于使用，适合做数据交换。后者则是全功能的XML解析器。
    哥更倾向于TingyXml.小巧啊！  RapidXml
TinyWebServer

WeChatRobot
PC版机器人，值得研究学习

openGL
redis 

Chromium
向左向右，怎么看现在只有Chromium是c++中最庞大的一个，自己在造轮子的时候，可以搜索下这个宝库，保证有各种型号的轮子。
Chromium涉及了几乎所有的平台，所以不仅能学到平台之上API的封装，还有包括Network的各种封装和借口，协议的C++的实现。
更甚至，webrtc，native client，sandbox，GPU，并行加速，debug，各种神奇的第三方的库，各种各样的技术，能潜心学深一个，就可以功力大增。

FreeNOS
这是我在大学的时候，接触完整学习的第一个开源的C++项目，当时简直是，各种惊叹，里面有太多值得学习的地方。
这是一个用C++实现的微内核的操作系统，各种宏内核中的服务作为一个独立的services在微内核中，基于消息的通信方式，这点其实跟mac内核中的mach那部分机制相似。
除了是一个操作系统的实现，另外从中也能很好的学习到OOP的设计方式，整个代码风格特别好，完全基于面相对象，还有一些常见的设计模式，在接触了这个开源项目之后，才了解，代码风格，注释，doxygen，scons，设计模式。
对于直接入手就啃Linux kernel的同学，个人觉得会门槛有点高，身体还不是特别棒的时候，直接攀登珠穆拉玛还是有点吃力的，可以先找个黄山爬爬。


红的发紫的项目，整个node.js 包括内部的核心V8都是C++的项目，完全的事件驱动，非阻塞IO，性能比nginx还快，可以说是把服务器彻底的榨干的节奏，这种设计模式，是现在比较流行的Reactor pattern ，concurrent computing。在构建一些大型的web services中，尤其凸显优势，现在移动互联网时代，在做app push services的时候，后端自己实现的推送服务，基本也是这种思路，An Open Source MQTT v3.1 Broker 并发量能到几十万，甚至对内核参数修改过后能到上百万。
Node.js另一个核心的组建是Marc Lehmann’s libev http://libev.schmorp.de , 基于event驱动的非阻塞IO库，在node-v0.9.0之后，node.js项目考虑到跨平台的实现，封装了一个项目libuv/libuv · GitHub, 

Linux based on (epoll)
windows based on IOCP
Unix (mac os x) based on kevent
学习下，也能用在自己做不同平台高性能网络

Mongo Database
值得学习的C语言开源项目
Libevent
libev是一个开源的事件驱动库，基于epoll，kqueue等OS提供的基础设施。其以高效出名，它可以将IO事件，定时器，和信号统一起来，统一放在事件处理这一套框架下处理。基于Reactor模式，效率较高，并且代码精简（4.15版本8000多行），是学习事件驱动编程的很好的资源。

 下载链接：https://github.com/libevent/libevent

Memcached
Memcached 是一个高性能的分布式内存对象缓存系统，用于动态Web应用以减轻数据库负载。它通过在内存中缓存数据和对象来减少读取数据库的次数，从而提供动态数据库驱动网站的速度。Memcached 基于一个存储键/值对的 hashmap。Memcached-1.4.7的代码量还是可以接受的，只有10K行左右。
 下载地址：http://memcached.org/

Redis
Redis 是一个使用 C 语言写成的，开源的 key-value 数据库。Redis支持的操作和数据类型比Memcached要多，现在主要用于缓存，支持主从同步机制，Redis的学习可以参考<>一书。

下载地址：http://redis.io/

Webbench
Webbench是一个在linux下使用的非常简单的网站压测工具。它使用fork()模拟多个客户端同时访问我们设定的URL，测试网站在压力下工作的性能，最多可以模拟3万个并发连接去测试网站的负载能力。Webbench使用C语言编写, 代码实在太简洁，源码加起来不到600行。

下载链接：https://github.com/LippiOuYang/WebBenchl

APR（Apache Portable Runtime）
这是由 Apache 社区维护的 C 开源库，主要提供操作系统相关的功能（文件系统、进程、线程、用户、IPC）。此外还提供了一些网络相关的功能。

APR 原先是 Apache Web 服务器的一个组成部分，后来独立出来，成为一个单独的开源项目。
 主页：https://apr.apache.org

NGINX
Nginx是由俄罗斯软件工程师Igor Sysoev开发的一个高性能的HTTP和反向代理服务器，具备IMAP/POP3和SMTP服务器功能。Nginx最大的特点是对高并发的支持和高效的负载均衡，在高并发的需求场景下，是Apache服务器不错的替代品。目前，包括新浪、腾讯等知名网站已经开始使用Nginx作为Web应用服务器。
 主页：http://nginx.org/en/download.html

Tinyhttpd
tinyhttpd是一个超轻量型Http Server，使用C语言开发，全部代码只有502行(包括注释)，附带一个简单的Client，可以通过阅读这段代码理解一个 Http Server 的本质。

下载链接：https://github.com/LippiOuYang/Tinyhttpd

cJSON
cJSON是C语言中的一个JSON编解码器，非常轻量级，C文件只有500多行，速度也非常理想。
 cJSON也存在几个弱点，虽然功能不是非常强大，但cJSON的小身板和速度是最值得赞赏的。其代码被非常好地维护着，结构也简单易懂，可以作为一个非常好的C语言项目进行学习。

项目主页:http://sourceforge.net/projects/cjson/

CMockery
cmockery是google发布的用于C单元测试的一个轻量级的框架。它很小巧，对其他开源包没有依赖，对被测试代码侵入性小。cmockery的源代码行数不到3K，你阅读一下will_return和mock的源代码就一目了然了。
 主要特点：

免费且开源，google提供技术支持；
轻量级的框架，使测试更加快速简单；
避免使用复杂的编译器特性，对老版本的编译器来讲，兼容性好;
并不强制要求待测代码必须依赖C99标准，这一特性对许多嵌入式系统的开发很有用
下载链接：http://code.google.com/p/cmockery/downloads/list

Lua
Lua很棒，Lua是巴西人发明的，这些都令我不爽，但是还不至于脸红，最多眼红。
 让我脸红的是Lua的源代码，百分之一百的ANSI C，一点都不掺杂。在任何支持ANSI C编译器的平台上都可以轻松编译通过。我试过，真是一点废话都没有。Lua的代码数量足够小，5.1.4仅仅1.5W行，去掉空白行和注释估计能到1W行。
 下载地址：http://www.lua.org/

SQLite
SQLite是一个开源的嵌入式关系数据库，实现自包容、零配置、支持事务的SQL数据库引擎。 其特点是高度便携、使用方便、结构紧凑、高效、可靠。足够小，大致3万行C代码，250K。
 下载地址：http://www.sqlite.org/ 。

UNIX v6
UNIX V6 的内核源代码包括设备驱动程序在内 约有1 万行，这个数量的源代码，初学者是能够充分理解的。有一种说法是一个人所能理解的代码量上限为1 万行，UNIX V6的内核源代码从数量上看正好在这个范围之内。看到这里，大家是不是也有“如果只有1万行的话没准儿我也能学会”的想法呢？
 另一方面，最近的操作系统，例如Linux 最新版的内核源代码据说超过了1000 万行。就算不是初学者，想完全理解全部代码基本上也是不可能的。

下载地址：http://minnie.tuhs.org/cgi-bin/utree.pl?file=V6

NETBSD
NetBSD是一个免费的，具有高度移植性的 UNIX-like 操作系统，是现行可移植平台最多的操作系统，可以在许多平台上执行，从 64bit alpha 服务器到手持设备和嵌入式设备。NetBSD计划的口号是：”Of course it runs NetBSD”。它设计简洁，代码规范，拥有众多先进特性，使得它在业界和学术界广受好评。由于简洁的设计和先进的特征，使得它在生产和研究方面，都有卓越的表现，而且它也有受使用者支持的完整的源代码。许多程序都可以很容易地通过NetBSD Packages Collection获得。

下载地址：http://www.netbsd.org/

值得学习的C++开源项目
LevelDb
LevelDb是谷歌两位大神级别的工程师发起的开源项目，简而言之，LevelDb是能够处理十亿级别规模Key-Value型数据持久性存储的C++ 程序库。
 它是一个持久化存储的KV系统，和Redis这种内存型的KV系统不同，LevelDb不会像Redis一样狂吃内存，而是将大部分数据存储到磁盘上。
 　　其次，LevleDb在存储数据时，是根据记录的key值有序存储的，就是说相邻的key值在存储文件中是依次顺序存储的，而应用可以自定义key大小比较函数，LevleDb会按照用户定义的比较函数依序存储这些记录。

主页:https://github.com/google/leveldb

Boost.Asio
它是异步输入输出的核心。 名字本身就说明了一切：Asio 意即异步输入/输出。该库可以让 C++ 异步地处理数据，且平台独立。异步数据处理就是指，任务触发后不需要等待它们完成。相反，Boost.Asio 会在任务完成时触发一个应用。异步任务的主要优点在于，在等待任务完成时不需要阻塞应用程序，可以去执行其它任务。

异步任务的典型例子是网络应用。如果数据被发送出去了，比如发送至 Internet，通常需要知道数据是否发送成功。 如果没有一个象 Boost.Asio 这样的库，就必须对函数的返回值进行求值。但是，这样就要求待至所有数据发送完毕，并得到一个确认或是错误代码。而使用 Boost.Asio，这个过程被分为两个单独的步骤：第一步是作为一个异步任务开始数据传输。 一旦传输完成，不论成功或是错误，应用程序都会在第二步中得到关于相应的结果通知.主要的区别在于，应用程序无需阻塞至传输完成，而可以在这段时间里执行其它操作。

主页：http://www.boost.org/doc/libs/1_58_0/doc/html/boost_asio.html

SGI STL
SGI STL是STL代码的经典实现版本，虽然很多编译器不直接使用这个版本，但是很多却在此基础之上进行改进的。比如GNU C++的标准库就是在此基础之上改进的。这份代码还有一个好处是有注释，代码书写非常规范，只要花些时间读懂它并非难事。

主页：https://www.sgi.com/tech/stl/download.html

Muduo
muduo 是一个基于 Reactor 模式的现代 C++ 网络库，它采用非阻塞 IO 模型，基于事件驱动和回调，原生支持多核多线程，适合编写 Linux 服务端多线程网络应用程序。

主页:https://github.com/chenshuo/muduo

Lua

SQLite

UNIX v6

NETBSD

值得学习的C++开源项目

LevelDb

Boost.Asio

SGI STL

Muduo



相应的c开源库有ffmpeg、mpeg4、aac、avc、libmad、mpeg1、flac、ac3、ac3、matroska著名的多媒体播放器 TCPMP 天下闻名的跨平台、嵌入式手持设备视频播放器，

网络开发类
gSOAP SOAP协议的C++支持库及代码生成工具。

GUI库
wxWidgets ：使用wxWidgets ，开发者可以基于同一套代码，为Win32, Mac OS X, GTK+, X11, Motif, WinCE等平台开发应用程序。wxWidgets库可以被C++, Python, Perl, and C#/.NET等开发语言使用。跟其它有些同样支持跨平台GUI开发工具不同，基于wxWidgets的应用，拥有真实本地化的视觉及使用效果——因 为，wxWidgets使用（各）平台原生的控件，而不是简单通过贴图去模拟。wxWidgets是使用广泛的，自由的，开源的，成熟的。

QT-------------界面（GUI）开发，支持C++/Java/Python/...多种语言。跨平台。最主要的好处是，API非常优 美！Qt本身也不仅仅只是做GUI编程，实际它基本上可以做OS-API可以做的任何事情。象网络/数据库/OpenGL/...都提供完美的支持。
      传统上Qt被认为是可移植的GUI库，但实际上Qt现在已经是一个比较完整的可移植应用程序框架了，其中包含了大量的工具，比如正则表达式、Web和 Socket类、2D和3D图形、XML解析、SQL类等，甚至还包括了一个完整的容器类库，不过其王牌还是GUI。在目前的跨平台GUI框架中，Qt成熟度最高，已经被一些大公司应用在关键产品中。由于Trolltech对Qt采用的dual license模式，该产品既可以从开源社区获得支持，又能够赚取足够的商业利润，因此其前景也令人比较有信心。            Qt的主要技术特色是其元对象模型。Qt实际上使用的并不是标准的C++，而是标准C++的一个扩展。它通过元对象模型扩展，实现了著名的signal/slot机制，而这一机制也成为Qt的最大特色和优势。     与Qt类似的可移植GUI框架还有wxWidget、FOX等

计算机视觉
OpenCV，因特尔自主的开源库。支持C/C++/Python接口。这个感兴趣的朋友可以玩一下。如果结合OpenCV，你可以做一些外行人觉得很酷的程序。比如说用它的人脸识别函数，来对你的摄像头进行处理，判断人的动作等

 图形图像处理
GDAL，处理大图像。　要是GIS专业的人肯定会语言到非常大的tif影像，动则几个GB的航空影像。GDAL对大图像的读写支持是非常棒的（像多波段的图像都可以搞定）。　　支持C++/Java/Python...
    国外开源的GIS软件QGIS就是用了gdal
    c的图形图像库较多，libjpeg、libpng、zlib、tiff、JBIG、最著名的开源形图像处理软件Cximage

九、密码及安全：OpenSSL    安全是今天进行C/C++编程无法回避和必须重视的问题。然而编写安全的应用程序，特别是跟网络相关的C/C++应用程序，是一件十分困难的事情。可以 说，整个业界目前在这个进程上仍然处于“初级阶段”。特别是涉及到大量的安全、密码学相关的算法、规范，如果让开发者自己摸索，其工作量和难度达到了不现
        实的程度。因此必须借助可靠的相关程序库才有可能提高程序的安全性。在这方面，OpenSSL是目前最好的选择，其内容之全面可靠，已经成为业界标杆。然 而，由于安全编程固有的复杂性，即使使用penSSL，开发工作仍然是非常繁琐的。因此我们也希望能够尽快看到更简单、更易用的C/C++安全程序库。

矩阵计算：MTL    自1995年以来，C++在科学计算领域当中取得了巨大的突破。这主要归功于template技术的高级应用，使得C++在科学计算的性能方面取得了巨大 的进步，一大批优秀的C++科学计算库涌现出来。比如Blitz++、POOMA、MTL、Boost::uBLAS。而这其中，MTL就功能丰富程度、
        性能、开发支持和成熟程度来讲，是比较突出的一个，因此可以优先考虑。值得一提的是，2002年，MTL与后来被Intel收购的KAI C++配合，曾经在性能评测中击败了FORTRAN。


 1、分布式对象中间件：ICE     ICE是分布式对象中间件领域里的后起之秀，可以大致地将其视为“改进版”的CORBA。目前应用在一些大型项目当中，其中包括波音公司主持的下一代陆军作战系统。      ICE的一个特别价值是其代码的范例意义。由于ICE的出现较晚，开发者比较系统地应用了新的C++编程风格，所以成为了研读C++代码的良好目标。
    2、消息中间件：ZeroMQ，总结的几种特性如下：
     1） 消息系统中，它差不多是最简洁的，只是个简洁的API，有n多种语言的绑定，没有专门的服务器；   2） 性能非常优越，远远高于RabbitMQ、ActiveMQ、MSMQ等；   3） 适合做分布式和并发应用。


配置管理：Lua    随着软件系统越来越复杂，对软件的可配置型提出了越来越高的要求。传统上只要通过命令行参数来配置的系统，现在可能需要越来越多的方式和机制。目前越来越 受欢迎、并且得到越来越多证实的做法，是将Lua嵌入到C/C++程序中，而用Lua程序作为配置脚本。这种做法的优势是，Lua语言强大灵活，可以适应
        复杂的配置要求。同时，Lua便于嵌入C/C++程序，而且编译执行速度非常快，可以说是目前解决C/C++程序配置管理问题的一个出色方案。

C++ 游戏引擎