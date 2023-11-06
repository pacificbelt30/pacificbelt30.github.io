---
title: "Git cloneなどremoteへのアクセス時にユーザ名とパスワードを毎回求められる話"
date: 2022-07-20T02:33:35+09:00
tags: ["linux","git"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

# Git cloneなどremoteへのアクセス時にユーザ名とパスワードを毎回求められる話
```
git clone https://github.com/xxxxxxxxx
```
などのようにhttpsで`git clone`するときや`git push`するとき，それがプライベートレポジトリだと最初に認証情報を求められる．

SSHで接続すると方法もあるが，外向きにSSHの通信が制限されているときには，httpsを使う必要が出てくる．

この認証を一度行った後に，
例えばWindowsの場合は認証情報を覚えているようなので入力をスキップすることができる．
それに対してLinuxは毎回認証情報を打たなければならない．
これまでこの挙動自体はgitの仕様だと思って，極力sshを使用するようにしてきたのだが，実際にはLinuxでも認証情報を保持することができた．

## gitの認証情報をキャッシュする
[ここ](https://docs.github.com/ja/get-started/getting-started-with-git/caching-your-github-credentials-in-gitA)にGit に GitHub の認証情報をキャッシュする方法が書いてある．
どうやらGCMという仕組みがあり，それを使用することで認証情報を保持しておくことができるらしいことがわかった．(AESの暗号利用モードではない)
Windowsの場合はデフォルトで入っていて，Linuxの場合は別でインストールする作業が必要になる．

## まとめ
やり方についてはリンクのとおりなのでこの記事で記述することはしないが，Linuxでも認証情報をキャッシュできることがわかったので，これからはhttpsでもgit cloneを使用してもsshでcloneするのと同じ使い勝手で使用できそうだと思われる．

## 追記
[HTTPS ポートを介して SSH する方法](https://docs.github.com/ja/authentication/troubleshooting-ssh/using-ssh-over-the-https-port)があった．
本来 SSH をする場合，`github.com` の 22番ポートにリクエストする必要があるが，`ssh.github.com` という `github.com` のサブドメインでは https のポートである 443番ポートに同じ鍵を用いて SSH ができる．
設定ファイルとしては以下のようになる．
```
Host github.com
  HostName ssh.github.com
  IdentityFile ~/.ssh/priv_key
  Port 443
  User git
```

22番ポートが塞がれている場合でも SSH できるようになったため，SSHの通信そのものがキャプチャされるような環境でないならばこちらの方法を用いるほうが便利に感じる．
