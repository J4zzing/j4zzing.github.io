# SS Server installation(CentOS7.x)

## （可选）一键安装脚本

脚本1：

```bash
yum -y install wget

wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```



脚本2：

```bash
yum -y install wget

wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
```

来源：[https://github.com/Alvin9999/new-pac/wiki/%E8%87%AA%E5%BB%BAss%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%95%99%E7%A8%8B](https://github.com/Alvin9999/new-pac/wiki/自建ss服务器教程)

## 安装pip

CentO S：`yum install python-setuptools && easy_install pip`

Debian/Ubuntu：`apt-get install python-pip`

## 安装Shadowsocks
`使用pip安装`：`pip install shadowsocks`

## 创建并编辑SS配置文件
`vi /etc/shadowsocks.json`

## SS服务器配置文件写法例举
```
{
    "server":"0.0.0.0",
    "server_port":2333,
    "local_port":1080,
    "password":"password",
    "timeout":600,
    "method":"rc-md5"
}
```

## 以保护进程模式启动SS服务器进程
`ssserver -c /etc/shadowsocks.json -d start`

## ss服务器自启动
1. 编辑启动脚本

	`vi /etc/systemd/system/shadowsocks.service`
	
	```
	[Unit]
	Description=Shadowsocks
	
	[Service]
	TimeoutStartSec=0
	ExecStart=/usr/bin/ssserver -c /etc/shadowsocks.json
	
	[Install]
	WantedBy=multi-user.target
	```

2. 启动shadowsocks服务  
	`systemctl enable shadowsocks`  
	`systemctl start shadowsocks`

3. 查看状态
`systemctl status shadowsocks -l`

## （可选）[BBR一键脚本](https://github.com/teddysun/across)

```bash
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh
```

## （可选）[魔改 BBR 一键脚本](https://github.com/tcp-nanqinlang/wiki/wiki/general)

>#CentOS 6/7  
#only 64 bit  
wget https://raw.githubusercontent.com/tcp-nanqinlang/general/master/General/CentOS/bash/tcp_nanqinlang-1.3.2.sh
bash tcp_nanqinlang-1.3.2.sh



## Linux实用工具
查看系统版本：`cat /etc/issue`

查看Linux内核版本：`uname -r`  

查看可用TCP拥塞控制算法：`sysctl net.ipv4.tcp_available_congestion_control`  

查看当前TCP拥塞控制算法：`sysctl net.ipv4.tcp_congestion_control`


## TroubleShooting
1. （可选）确认SS已经启动
	`netstat -anp |grep <端口号>`
2. curl --socks5 127.0.0.1:1080 http://httpbin.org/ip

### CentOS未找到netstat命令
`yum search ifconfig`
通过`yum search`这个命令我们发现`ifconfig`这个命令是在`net-tools.x86_64`这个包里，接下来我们安装这个包就行了

运行`yum install net-tools`就OK了