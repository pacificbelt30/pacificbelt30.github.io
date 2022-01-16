---
title: "pacmanでパッケージを更新したときに「」"
date: 2022-01-17T01:47:42+09:00
tags: ["linux"]
featured_image: ""
description: ""
toc: true
isCJKLanguage: true
---

## 問題
いつもどおり数週間放置したパッケージの更新を行ったとき，
めちゃくちゃエラーが出た．
```
エラー: 処理を完了できませんでした (衝突しているファイル)
gtop: /usr/lib/node_modules/gtop/CLI.md がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/.github/workflows/visual-studio.yml がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/.bin/color-support がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/ansi-regex/index.d.ts がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/aproba/CHANGELOG.md がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/are-we-there-yet/LICENSE.md がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/are-we-there-yet/lib/index.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/are-we-there-yet/lib/tracker-base.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/are-we-there-yet/lib/tracker-group.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/are-we-there-yet/lib/tracker-stream.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/are-we-there-yet/lib/tracker.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/color-support/LICENSE がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/color-support/README.md がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/color-support/bin.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/color-support/browser.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/color-support/index.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/color-support/package.json がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/emoji-regex/LICENSE-MIT.txt がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/emoji-regex/README.md がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/emoji-regex/es2015/index.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/emoji-regex/es2015/text.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/emoji-regex/index.d.ts がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/emoji-regex/index.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/emoji-regex/package.json がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/emoji-regex/text.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/LICENSE.md がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/base-theme.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/demo.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/error.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/has-color.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/index.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/plumbing.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/process.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/progress-bar.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/render-template.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/set-immediate.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/set-interval.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/spin.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/template-item.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/theme-set.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/themes.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/gauge/lib/wide-truncate.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/is-fullwidth-code-point/index.d.ts がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/npmlog/LICENSE.md がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/npmlog/lib/log.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/errors-browser.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/errors.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/experimentalWarning.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/lib/internal/streams/async_iterator.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/lib/internal/streams/buffer_list.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/lib/internal/streams/end-of-stream.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/lib/internal/streams/from-browser.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/lib/internal/streams/from.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/lib/internal/streams/pipeline.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/readable-stream/lib/internal/streams/state.js がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/string-width/index.d.ts がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/node_modules/strip-ansi/index.d.ts がファイルシステムに存在しています
node-gyp: /usr/lib/node_modules/node-gyp/test/fixtures/nodedir/include/node/config.gypi がファイルシステムに存在しています
エラーが発生したため、パッケージは更新されませんでした。
```
なんか前にも出た気がするのでなんとかなるやろっということで検索履歴をたどる．

## 解決策
これが正攻法ではない気がするけど
ファイルが存在していて更新ができないなら強制的に上書きすればよいということで
```
sudo pacman -S npm --overwrite='*'
```
とかやってパッケージのインストール時にファイルを上書きするようにしたらうまく行った．
これをエラーが出てるnpm,node-gyp,gtopについて実行する．
ここまでやったら再び
```
sudo pacman -Syu
```
でパッケージの更新を行うと無事更新が通った．

## 最後に
今回は比較的すぐに解決できたけど，またすぐに遭遇して履歴をたどるめんどくさい作業を行う必要がありそうなのでここにまとめておく．
実際npmをpacmanで管理することがじつは間違ってたりするんですかね．

## 参考
[npm update error in arch](https://github.com/nodesource/distributions/issues/636)
[Failed to commit transaction (conflicting files) when updating packages on Manjaro](https://stackoverflow.com/questions/67353216/failed-to-commit-transaction-conflicting-files-when-updating-packages-on-manja)

