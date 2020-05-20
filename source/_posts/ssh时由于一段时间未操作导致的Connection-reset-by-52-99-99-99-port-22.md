---
title: ssh时由于一段时间未操作导致的Connection reset by x.x.x.x port 22
date: 2020-05-20 23:24:23
tags:Linux SSH
---

来源：https://unix.stackexchange.com/questions/334437/ssh-connection-reset-after-idle-for-some-time

使用`ssh -o TCPKeepAlive=true root@host.com`

好像还是会受到网络波动的影响？

