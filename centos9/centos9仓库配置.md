# centos-stream-9仓库配置

epel源:
```bash
dnf config-manager --set-enabled crb
dnf install epel-release epel-next-release
```


yum源报错：
```bash
# yum install yum-utils 
Loaded plugins: fastestmirror, product-id, search-disabled-repos, subscription-manager

This system is not registered with an entitlement server. You can use subscription-manager to register.

Loading mirror speeds from cached hostfile
```
解决方法:
```bash
# vim /etc/yum/pluginconf.d/subscription-manager.conf
[main]
enabled=0
```

# 参考资料
- [yum提示报错](https://www.cnblogs.com/ajunyu/p/13297449.html)
- [CentOS Stream 9 和 RHEL 9 epel源的添加](https://shipengliang.com/software-exp/centos-stream-9-%E5%92%8C-rhel-9-epel%E6%BA%90%E7%9A%84%E6%B7%BB%E5%8A%A0.html)
