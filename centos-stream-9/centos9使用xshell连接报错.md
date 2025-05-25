# centos-stream-9使用xshell连接报错

xshell连接时提示: SSH服务拒绝了密码。请再试一次。
解决方法：
```bash
PermitRootLogin yes
vim /etc/ssh/sshd_config
PermitRootLogin yesvim /etc/ssh/sshd_config
PermitRootLogin yes
```

# 参考资料
-[centos-stream-9使用xshell连接报错](https://blog.csdn.net/peakccy/article/details/131453755)