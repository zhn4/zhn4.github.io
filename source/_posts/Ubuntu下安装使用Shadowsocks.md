---
title: Ubuntu下安装使用Shadowsocks
date: 2016-07-07 16:08:00
tags:
---
### Ubuntu下安装使用Shadowsocks

- ubuntu安装shadowsocks
``` bash
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```

- shadowsocks没有菜单栏解决办法
https://bugs.launchpad.net/ubuntu/+source/appmenu-qt5/+bug/1307619
``` bash
sudo apt-get remove appmenu-qt5

```

- 安装proxychains-ng
``` bash
mkdir -p ~/softwares
cd ~/softwares
git clone git@github.com:rofl0r/proxychains-ng.git
cd proxychains-ng
./configure --prefix=/usr --sysconfdir=/etc
make clean
make
sudo make install
```

- 修改proxychains文件
``` bash
vim ~/.proxychains-ng/proxychains.conf
```

- 复制粘贴一下内容
```bash
strict_chain
proxy_dns
remote_dns_subnet 224
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.0/255.0.0.0
quiet_mode

[ProxyList]
socks5  127.0.0.1 1080
```
