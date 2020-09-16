---
title: 各个Unix系统仓库国内源
date: 2020-07-26 15:51:12
tags: 
- Unix
---

## 国内源主页

https://mirrors.tuna.tsinghua.edu.cn/

## Debian

介绍

https://wiki.debian.org/SourcesList

https://manpages.debian.org/buster/apt/sources.list.5.en.html

Debian 全球镜像站

https://www.debian.org/mirror/list

### 如何选择最快的镜像站

https://linuxconfig.org/how-to-select-the-fastest-apt-mirror-on-ubuntu-linux

Debian netselect

https://github.com/apenwarr/netselect

> ```
> netselect determines several facts about all of the hosts given on the
> command line, much faster you would if you manually tried to use ping and
> traceroute. 
> ```

### 使用方法

```shell
netselect -vv mirrors.tuna.tsinghua.edu.cn mirrors.ustc.edu.cn mirrors.aliyun.com mirrors.163.com
```

```shell
netselect -vv https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ https://mirrors.ustc.edu.cn/ubuntu/ http://mirrors.aliyun.com/ubuntu/ http://mirrors.163.com/ubuntu/
```



## Ubuntu

### 解决方案

https://www.jianshu.com/p/126d51514097

https://zhuanlan.zhihu.com/p/61228593

### Ubuntu国内仓库源

```
# 清华源
https://mirrors.tuna.tsinghua.edu.cn/ubuntu/
# 中科大源
https://mirrors.ustc.edu.cn/ubuntu/
# 阿里源
http://mirrors.aliyun.com/ubuntu/
# 163源
http://mirrors.163.com/ubuntu/
```

