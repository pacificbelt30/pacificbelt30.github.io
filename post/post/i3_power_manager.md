---
title: "xfce4のディスプレイの設定が適用されない"
date: 2021-12-07T13:49:44+09:00
tags: ["linux","i3","xfce4"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

## EndeavorOSのスクリーンセーバーの設定がうまく行かない話

## 現状怪しいところ
```sh
$ ps -aux | grep xfce4
user         844  0.0  0.6 507980 48540 ?        Sl   13:24   0:00 xfce4-power-manager
user         847  0.0  0.3 234756 30000 ?        Sl   13:24   0:00 xfce4-screensaver
user         862  0.0  0.0 229348  5976 ?        Sl   13:24   0:00 /usr/lib/xfce4/xfconf/xfconfd
user        4391  0.7  0.8 668976 69056 ?        Rl   13:25   0:11 xfce4-terminal
user       43271  0.0  0.0   7548  2460 pts/0    S+   13:51   0:00 grep --color=auto xfce4
```
autostartでscreensaverとpower-managerが起動しているのがよくなさそう
- dex
- /etc/xdg/autostart/
- /etc/lightdm/Xsession

