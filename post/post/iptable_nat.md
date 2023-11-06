---
title: "iptableでssh転送"
date: 2021-12-01T13:51:10+09:00
tags: ["linux","ssh"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

## summary
```sh
sudo iptables -t nat -A PREROUTING -i eth0 -d 192.168.1.30 -p tcp -m tcp --dport 22 -j DNAT --to-destination 192.168.30.3:22
sudo iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.1.0/24 -p tcp -m tcp --dport 22 -j MASQUERADE
sudo iptables-save > /etc/iptables.ipv4.nat
```

## 下準備
今回はiptableコマンドを使うので
```sh
iptable --help
```
を実行して，iptableコマンドが使用可能なことを確認しておく．

## iptableでssh転送
sshを転送するための設定を行う．
次のコマンドを実行し，
ipの転送設定を行う．
IPアドレスは任意の値にする．
```sh
sudo iptables -t nat -A PREROUTING -i eth0 -d 192.168.1.30 -p tcp -m tcp --dport 22 -j DNAT --to-destination 192.168.30.3:22
sudo iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.1.0/24 -p tcp -m tcp --dport 22 -j MASQUERADE
```
1つ目のコマンド
`iptables -t nat -A PREROUTING -i eth0 -d 192.168.1.30 -p tcp -m tcp --dport 22 -j DNAT --to-destination 192.168.30.3:22`
は`-d`のあとに指定したIPアドレスに対するアクセスを`--to-destination`のあとに指定したIPアドレスに転送する設定を表している．
2つ目のコマンド
`iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.1.0/24 -p tcp -m tcp --dport 22 -j MASQUERADE`
は`-s`のあとに指定したIPアドレスの端末と1つ目のコマンドで指定したIPアドレスの端末とをつなぐ役割？（よくわかってない）

これを実行するとsshの転送ができるはず．

## 設定の永続化
[ここ](https://pacificbelt30.github.io/post/raspi_ap/)のやり方でアクセスポイントを構築した場合は
```sh
sudo iptables-save > /etc/iptables.ipv4.nat
```
を実行すると良い．

## 最後に
できない人は自分で調べて

