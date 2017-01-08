# Python

根据趋势，以使用`Python 3`为主。

## 安装

### Linux 下编译

编译的依赖包：

```
yum install gdbm-devel sqlite-devel xz-devel gcc gcc-c++ make bzip2-devel openssl-devel
```

编译:

```
./configure --prefix=/usr/local --enable-shared --enable-ipv6
make -j10
sudo make install 
```

### macOS

```
brew install python3
```

## 包

使用`pip`安装

```
pip install numpy scipy matplotlib pandas ipython jupyter astropy
```
