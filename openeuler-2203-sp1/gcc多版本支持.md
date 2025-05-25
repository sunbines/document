# gcc多版本支持

为了和默认 GCC 安装做出区分，防止多版本 GCC 的安装和默认 GCC 的安装依赖库冲突，gcc-12 的多版本软件包名以 “gcc-toolset-12-” 为前缀，后面接上原有 GCC 软件包名。
默认编译器 gcc-10.3.1，安装路径为 /usr/:
```bash
yum install -y gcc gcc-c++ gcc-gfortran
```
多版本编译器 gcc-12，安装路径为/opt/openEuler/gcc-toolset-12/root/usr/ ：
```bash
yum install -y gcc-toolset-12-gcc*
```
使用方法: gcc-12 多版本编译器软件包安装在/opt/openEuler/gcc-toolset-12/root/usr/下，因此可使用如下命令使用软件包：
```bash
export PATH=/opt/openEuler/gcc-toolset-12/root/usr/bin/:$PATH
export LD_LIBRARY_PATH=/opt/openEuler/gcc-toolset-12/root/usr/lib64/:$LD_LIBRARY_PATH
```
注意：多版本编译器 gcc-12 仅用于支持 GCC 10.3.1 不支持的 OpenMP 4.5 规范，其他特性建议使用默认 gcc-10.3.1 防止发生未知编译错误。


# 参考资料
- [gcc多版本支持](https://docs.openeuler.openatom.cn/zh/docs/22.03_LTS_SP3/docs/GCC/GCC%E5%A4%9A%E7%89%88%E6%9C%AC%E6%94%AF%E6%8C%81%E7%94%A8%E6%88%B7%E6%8C%87%E5%8D%97.html)

