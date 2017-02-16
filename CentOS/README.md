# CentOS 7

**最小化安装**

### 系统配置

- 禁掉`selinux`
- 更新`Iptables`

```
systemctl disable firewalld
systemctl stop firewalld

yum -y install iptables-services

systemctl start iptables
systemctl start ip6tables
systemctl enable iptables
systemctl enable ip6tables
```

下来就可以修改`/etc/sysconfig/iptable`来进行端口控制了

- 安装`netstat`等工具管理网络

```
yum -y install net-tools
``` 

- 禁止一些服务

```
systemctl disable NetworkManager
systemctl disable NetworkManager-wait-online
```

- ntpdate 服务

根据需要修改`/etc/ntp/step-tickers` 第一行为主时间服务器，第二行为备用。

```
systemctl enable ntpdate
````

### 软件安装

```
yum -y install vim gcc gcc-c++ make gcc-gfortran ntpdate rsync
yum -y install gperftools-devel.x86_64 bzip2 bzip2-devel
yum -y install openssl-devel python-devel 
yum -y install bison flex readline-devel geoip-devel

```

### 编译

```
./configure --prefix=/usr/local --with-pgport=5000 --with-openssl --with-python --enable-thread-safety --with-wal-blocksize=32 --with-blocksize=32 --with-wal-segsize=32
```

```
./configure --prefix=/opt/nginx --user=www --group=www --with-ipv6  --with-http_ssl_module  --with-http_realip_module --with-http_geoip_module     --with-http_gunzip_module  --with-http_gzip_static_module    --with-http_random_index_module --with-http_degradation_module   --with-http_secure_link_module --with-http_stub_status_module  --with-http_addition_module --with-http_addition_module   --with-google_perftools_module   --http-log-path=/data/log/http/access.log    --error-log-path=/data/log/http/error.log  --sbin-path=/usr/local/sbin/nginx --conf-path=/usr/local/etc/nginx/nginx.conf --pid-path=/var/run/nginx.pid
```

### Multipath

`/etc/multipath.conf`

```
defaults {
  user_friendly_names yes
}
blacklist {
  devnode "^sd[a-b]"
}
```

查看: `multipath -ll`