# vmware虚拟机安装openEuler

设置网卡
![图片](https://raw.githubusercontent.com/sunbines/images/main/2025/2025-blog-0001d49189ee65159dc08902352903f06400.png#pic_center=100x600)

<img src="https://raw.githubusercontent.com/sunbines/images/main/2025/2025-blog-0001d49189ee65159dc08902352903f06400.png" width="800px">

<br>

设置`/etc/sysconfig/network-scripts/ifcfg-ens192`配置网卡文件：
```bash
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
NAME=ens192
UUID=06f6fb63-4b67-4b99-b177-8301e7777749
DEVICE=ens192
ONBOOT=yes
IPADDR=192.168.0.101
GATEWAY=192.168.0.1
NETMASK=255.255.255.0
DNS1=8.8.8.8
DNS2=114.114.114.114
```
重启网卡
```bash
systemctl restart NetworkManager
```