---
title: "i3blocksに常駐ソフトが表示されない"
date: 2022-01-17T08:34:09+09:00
tags: ["linux","i3"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

## 解決策
[ここ](https://www.reddit.com/r/i3wm/comments/3rrju7/nmapplet_not_showing_up/)
に書いてあるとおり
i3の設定で
```
tray_output primary
```
としている場合，primaryが認識されていない（設定されていない）ためトレイに常駐ソフトが表示されない．
そのため，xrandrを用いてprimaryモニタの設定を行う．
まず，
```
xrandr
```
と実行すると現在接続されているモニタの情報を見ることができる．
その中からprimaryに設定したいモニタの名前を控えておいて，
次のコマンドを実行してprimaryモニタを設定する．
```
xrandr --output <name> --primary
```
<name>にはモニタの名前が入る．
自分の場合は
```
xrandr --output LVDS-1 --primary
```
と実行するとトレイに常駐ソフトが表示されるようになった．

