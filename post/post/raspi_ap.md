---
title: "ラズパイをWiFiのアクセスポイントとして使う方法"
date: 2021-11-23T20:06:54+09:00
tags: ["Seminar","RaspberryPi"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---
# ラズパイをWiFiのアクセスポイントとして使う方法
まず，
```
ifconfig
```
と打って，無線LANが使えることを確認

wlan0などが見つからない場合は
```
rfkill list
```
と打って，
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```
無線LANがブロックされていないかを確認する．

```
rfkill unblock all
```
とか打っておいて，無線LANのソフトブロックを外しておく．

あとは
[ここ](https://www.itmedia.co.jp/news/articles/2008/14/news042.html)
