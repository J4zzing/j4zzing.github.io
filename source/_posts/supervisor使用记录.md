---
title: supervisor使用记录
date: 2020-05-10 17:03:16
tags:
- Linux
---

### 配置文件

```配置文件
[program:x]
command=
directory=
autostart=
autorestart=
stdout_logfile=
stderr_logfile=


```



### 注意

不要在.conf文件中使用`~`符号

更新conf文件之后不建议使用restart。使用`supervisorctl update`