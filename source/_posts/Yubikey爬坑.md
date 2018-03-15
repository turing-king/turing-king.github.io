---
title: Yubikey爬坑
date: 2018-03-15 14:03:48
tags: [Yubikey,ArchLinux]
---
#Yubikey爬坑记录

我的电脑系统是Archlinux，之前买的yubikey配置好就放一边了，长时间没有用都忘记了怎么操作。于是乎拿出来玩一下，但是电脑无论怎么搞都无法使用普通用户查看信息，使用root账户倒是可以，但是操作就会报错。于是爬坑了。

首先解决权问题 参考这篇文章
[如何修改 Linux 设备访问权限](https://zhuanlan.zhihu.com/p/26718021)

权限问题解决了，但是还是不行啊，于是求助万能的谷歌。搜到了archlinux社区的一片帖子
[Cannot connect to gpg smartcard with non-root user](https://bbs.archlinux.org/viewtopic.php?id=222401)

但是，还是不行，我压根就没有pcsd这个服务，在我查看archlinux官方yubikey文档的时候，我发现了这个东西
[GnuPG only setups adn GnuPG witch pcacd](https://wiki.archlinux.org/index.php/GnuPG#Smartcards)

于是乎装上了 `libusb-compat` 和 `pcsclite` 还有`ccid `,之后启用pcsc服务，现在问题完美解决
