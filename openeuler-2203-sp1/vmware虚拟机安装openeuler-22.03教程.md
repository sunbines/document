# vmware虚拟机安装openeuler-22.03教程
`250GiB`硬盘容量分区方案如下图所示:

| 目录   | 容量     | 文件格式 |
|--------|----------|----------|
| /boot  | 2 GiB    | xfs      |
| /home  | 18 GiB   | xfs      |
| /var   | 30 GiB   | xfs      |
| /      | 200 GiB  | xfs      |

设置网卡:

<img src="https://raw.githubusercontent.com/sunbines/images/main/2025/01/img_02.png"/>

<br>
网卡配置文件`/etc/sysconfig/network-scripts/ifcfg-ens33`填写如下：

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
NAME=ens33
UUID=4686bb8a-8b97-45e7-b548-7ab8b3fce2fd
DEVICE=ens33
ONBOOT=yes
IPADDR=192.168.5.15
NETMASK=255.255.255.0
GATEWAY=192.168.5.2
DNS1=8.8.8.8
DNS2=114.114.114.114
```
重启网卡：
```bash
systemctl restart NetworkManager
```
