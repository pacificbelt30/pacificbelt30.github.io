---
title: "Sambaの設定"
date: 2021-12-01T13:24:24+09:00
tags: ["samba","linux"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

## summary
sambaをインストールして，設定を書く．
ゲストログインをできるようにしたい場合は`guest ok=yes`,`map to guest=Bad User`などを指定する．

## 下準備
以下の環境を想定
- RaspberryPi 3
- RaspberryPi OS lite

まず，sambaをインストールする．
```sh
sudo apt install samba
```

インストール後にsambaを有効化する．
```sh
systemctl start samba
systemctl enable samba
```
インストール直後はsambaのデフォルトの設定が適用された状態で
このままでも使うことはできるが，
ゲストアクセスなどを許可するために設定を行う．

## samba設定
`/etc/samba/smb.conf`をvimやnanoなどを用いて開き，
以下の設定を記述する．
root所有の設定ファイルを書き換えるので
```
cp /etc/samba/smb.conf /etc/samba/smb.conf.org
```
などとして予めデフォルトの設定をバックアップしておくと良い．

```conf
#======================= Global Settings =======================
[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP # Sambaの所属するワークグループ

#### Networking ####
   ;interfaces = 127.0.0.0/8 192.168.30.0/24 eth0
   interfaces = 192.168.30.0/24 wlan0 # 送信したいインターフェースのアドレス
   bind interfaces only = yes # よくわからない
   map to guest = Bad User # 不正なパスワードによるユーザのログインは拒否する，ユーザがない場合はゲスト扱い

#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m # log置き場

   max log size = 1000

   logging = file
   panic action = /usr/share/samba/panic-action %d # sambaクラッシュ時の動作

####### Authentication #######
   server role = standalone server 
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes

#======================= Share Definitions =======================
[Share]
   comment = Home Directories
   path = /home/pi/smb # ディレクトリまでのパス
   browseable = yes # エクスプローラーに表示する
   guest ok = yes # ゲストアクセスを許可
   guest only = yes # すべてのユーザをゲストとする

   read only = yes # 読み取りのみ

   create mask = 0755 # 権限設定 所有者のみ書き込み可能

   directory mask = 0755 # 権限設定 
```
設定を記述したらファイルを保存し，
sambaを再起動する．
```
systemctl restart samba
```
再起動後は
```
systemctl status samba
```
でsambaの状態を確認し，
他の端末のエクスプローラーなどのファイルマネージャからアクセスしてファイルが閲覧できるかを確認する．

## 参考
[/etc/samba/smb.conf 日本語訳 - Qiita](https://qiita.com/JhonnyBravo/items/6a68972cf5962a3c5afd)
