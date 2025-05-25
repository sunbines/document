
- [centos-stream-8默认仓库可配置](#centos-stream-8默认仓库可配置)
- [参考资料](#参考资料)

# centos-stream-8默认仓库可配置
```bash
CentOS-Stream-AppStream.repo
CentOS-Stream-BaseOS.repo
CentOS-Stream-Debuginfo.repo
CentOS-Stream-Extras-common.repo
CentOS-Stream-Extras.repo
CentOS-Stream-HighAvailability.repo
CentOS-Stream-Media.repo
CentOS-Stream-NFV.repo
CentOS-Stream-PowerTools.repo
CentOS-Stream-RealTime.repo
CentOS-Stream-ResilientStorage.repo
CentOS-Stream-Sources.repo
```

centos stream 8官方已经不再维护，导致该系统官方源实效，可以使用阿里云源进行替换：在修改配置文件前，创建一个备份文件，文件名加上.bak后缀。例如CentOS-Base.repo的备份会命名为 CentOS-Base.repo.bak
```bash
minorver=8-stream
sudo sed -e "s|^mirrorlist=|#mirrorlist=|g" \
         -e "s|^#baseurl=http://mirror.centos.org/\$contentdir/\$stream|baseurl=https://mirrors.aliyun.com/centos-vault/$minorver|g" \
         -i.bak /etc/yum.repos.d/CentOS-*.repo
```
如果不需要生成备份文件，可以直接去掉 -i.bak 参数中的 .bak，只保留 -i 即可。这会直接修改文件而不保留备份。修改后的命令如下：
```bash
minorver=8-stream
sudo sed -e "s|^mirrorlist=|#mirrorlist=|g" \
         -e "s|^#baseurl=http://mirror.centos.org/\$contentdir/\$stream|baseurl=https://mirrors.aliyun.com/centos-vault/$minorver|g" \
         -i /etc/yum.repos.d/CentOS-*.repo
```


配置epel源:
```bash
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
```

在CentOS/RHEL 8系统服务器上提供的PowerTools资源库提供了开发者相关的工具和库。一些常见的EPEL包依赖于PowerTools提供的包，因此，如果你在CentOS系统上设置了EPEL库，建议你启用PowerTools库。因此，如果你已经在CentOS系统上设置了EPEL资源库，建议你也启用PowerTools。要在 CentOS/RHEL 8 上启用 PowerTools 仓库，你可以使用 DNF 的 config-manager 插件，它可以管理各种 DNF 配置选项，包括添加/删除或启用/禁用仓库。

要安装config-manager插件，运行以下命令。
```bash
yum install dnf-plugins-core
```
使用DNF启用PowerTools配置管理器。CentOS/RHEL 8 已经添加了 PowerTools 存储库。因此,只需要启用它，执行如下所示：
```bash
dnf config-manager --set-enabled powertools
```
验证是否已成功启用PowerTools:
```bash
[root@stor01 ~]# dnf repolist
repo id                                                        repo name
appstream                                                      CentOS Stream 8 - AppStream
baseos                                                         CentOS Stream 8 - BaseOS
epel                                                           Extra Packages for Enterprise Linux 8 - x86_64
extras                                                         CentOS Stream 8 - Extras
extras-common                                                  CentOS Stream 8 - Extras common packages
powertools                                                     CentOS Stream 8 - PowerTools
```

配置ceph源:
```bash
#下载 Ceph 存储系统的 RPM 安装包
wget https://download.ceph.com/rpm-pacific/el8/noarch/ceph-release-1-1.el8.noarch.rpm --no-check-certificate
#rpm安装ceph存储系统
rpm -vih ceph-release-1-1.el8.noarch.rpm
```
* 可以安装`python3-grpcio-1.26.0-1.el8.x86_64`


# 参考资料
* [如何在CentOS8服务器上启用PowerTools](https://www.a5idc.com/helpcontent/232.html)
* [centos8stream 修改为阿里云yum源](https://blog.csdn.net/ly1358152944/article/details/141862695)


