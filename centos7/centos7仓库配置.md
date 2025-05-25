# centos7仓库配置
默认仓库配置:
```bash
CentOS-Base.repo
CentOS-CR.repo
CentOS-Debuginfo.repo
CentOS-fasttrack.repo
CentOS-Media.repo
CentOS-Sources.repo
CentOS-Vault.repo
CentOS-x86_64-kernel.repo
```

1. 配置epel.repo源
```bash
##  使用阿里提供的epel源
wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo
```

2. 配置centos-sclo-rh.repo源
```bash
[centos-sclo-rh]
name=CentOS-7 - SCLo rh
baseurl=https://mirrors.aliyun.com/centos/7/sclo/x86_64/rh/
gpgcheck=0
enabled=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-SCLo
```
安装gcc-11、g++-11
```bash
yum install devtoolset-11-gcc.x86_64 devtoolset-11-gcc-c++.x86_64
## 或者source /opt/rh/devtoolset-11/enable
scl enable devtoolset-11 bash
```

3. 配置/CentOS-Base.repo源
```bash
##  备份 /etc/yum.repos.d/CentOS-Base.repo
sudo cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
##  更换为阿里源
sudo curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
```

4. 配置ceph.repo源
```bash
[storage]
name=CentOS-7 - storage
baseurl=https://mirrors.aliyun.com/centos/7/storage/x86_64/ceph-nautilus
gpgcheck=0
enabled=1
gpgkey=http://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-Official
```

# 参考资料
 - [centos7的yum使用国内源阿里源163源等提高下载速度](https://juejin.cn/post/7137022034889932808)
 - [centos 7 更换为阿里云yum源](https://www.cnblogs.com/riverhan/articles/18298541)