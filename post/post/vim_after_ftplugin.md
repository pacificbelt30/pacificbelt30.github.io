---
title: "Vim_after_ftplugin"
date: 2021-12-01T09:37:52+09:00
tags: ["vim","linux"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

## summary
vimの設定は`runtimepath`に設定されている順に読み込まれていき，
衝突する部分は上書きされるのでデフォルトの設定を上書きしたい場合は
`runtimepath`の後ろの方のpath上に書きましょう．

## ファイルタイプごとの設定が効かない
とあるファイル編集中にインデントがおかしいことに気がついたため，
`init.vim`を確認したものの，そこにある記述とインデントの幅が合わない．
原因はわからないもののとりあえず，ファイルタイプの設定に書けば適用されるだろうということで
`~/.config/nvim/ftplugin/`以下にインデントの設定を記述した．
これで万事解決かと思い，再度ファイルを編集するもインデントは治っていなかったため，
本格的にどこで設定が書き換わっているかを調査することになった．

## 
vimには最後に値がsetされた部分をみるために`:verbose`コマンドが用意されている．
これを用いて`tabstop`が最後に変更された部分を見ると
```vim
:verbose set tabstop
  -> tabstop=4
      最後にセットしたスクリプト: /usr/share/nvim/runtime/ftplugin/ line 41
```
となっていて，`.config/nvim`以下の`ftplugin`ディレクトリの設定ではない他の設定が読み込まれていた．

vimの設定の読み込み順について調べると
どうやら`runtimepath`に設定されているpathを上から順に読み込んでいく形であり，
今回のケースでは`.config/nvim`以下の`ftplugin`ディレクトリの設定よりもあとに他の設定が読み込まれ書き換わっていた．

## 解決法
`.config/nvim/ftplugin`の設定があとから上書きされてしまうならさらにそれよりもあとから上書きしてやれば良い．
ということで，
```vim
:set runtimepath
```
を実行し，出力された`runtimepath`の比較的下の方にあるpathに新しく設定ファイルを置くことにする．
今回は`~/.config/nvim/after`以下に`ftplugin/`ディレクトリを作成し，その中にファイルを置くことにした．

`.config/nvim/ftplugin`に置いていたファイルを`~/.config/nvim/after/ftplugin/`にコピーし，
最後にセットされた箇所を確認すると
```
:verbose set tabstop
  -> tabstop=2
    最後にセットしたスクリプト: ~/.config/nvim/after/ftplugin/rust.vim line 41
```
というわけで設定を適用することができた．

## 最後に
- `runtimepath`と設定の読み込み順が重要なことを知ることができた．
- これからはファイルタイプごとの設定は`~/.config/nvim/after/ftplugin/`に書いていく．



