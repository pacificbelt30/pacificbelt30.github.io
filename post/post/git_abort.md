---
title: "Gitでmergeを取り消す方法"
date: 2021-12-01T01:46:53+09:00
tags: ["github","git"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

## 背景
とあるファイルをWindows上で編集，違うブランチとしてコミットし，
それをLinux上で
```sh
git merge <branch>
```
を実行し，マージを行う時，
コンフリクトが起こった．
コンフリクトの起こったファイルの中身を見ると
ソースコード全行が該当箇所となっていた．
原因はファイルを開いたときから明らかでそれぞれのブランチでファイルの改行コードが違うため（WindowsはCRLF,LinuxはLF），コンフリクトが起こっていた．
ほとんど内容が一緒で改行コードが違うだけでいちいちconflictの解消作業を行うのはさすがに面倒なので
mergeを行う前まで状態を戻したくなった．

## mergeを取り消す
結果からいうと
mergeを取り消すには
```sh
git merge --abort
```
を実行すれば良い．

## 終わりに
vscode上で改行コードを変更しているにも関わらず，何故かCRLFのままなのは何故だろうか．


