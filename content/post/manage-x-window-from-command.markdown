+++
categories = ["x window system", "linux"]
date = "2017-05-07T23:03:18+09:00"
description = ""
keywords = []
title = "X Window Systemのウィンドウをコマンドであれこれして見えないウィンドウを使えるようにする"
draft = true

+++

OS XでInkscape起動したらどっかに飛んで行って操作できなくなったりSSH越しにEclipse起動したらめちゃくちゃ小さくなって使えなかったりしたので書きます。

記事のゴール: 見えないウィンドウを使えるようにする。

<!--more-->

# Archで使うコマンドを入れる

`pacman -S xorg-xlsclients xorg-xwininfo xdotool`

# ウィンドウの一覧を取得する

`xlsclients -l`で取得。`WINDOW_ID`を使ってウィンドウの詳細情報を取得する。

環境: xlsclients 1.1.3

```
Window WINDOW_ID:
  Machine:  マシン名
  Name:  ウィンドウ名
  Icon Name:  eclipse
  Command:  コマンド名
  Instance/Class:  クラスヒント
```

# ウィンドウのサイズや場所を変更する

先程得た`WINDOW_ID`を使って`xwininfo -id WINDOW_ID`を実行しよくなさそうなパラメータを変える。
例えば、`Width`や`Height`が極端に大きい/小さいならサイズを変える、`upper-left X,Y`が-なら場所を変える等。

## サイズ変更

`xdotool windowsize WINDOW_ID WIDTH HEIGHT`

### デカすぎるので変更

見えるなら`xdotool`で`WINDOW_ID`をいちいち調べなくてもクリックして選択みたいなことができる。

## 場所変更

`xdotool windowmove WINDOW_ID WIDTH HEIGHT`

# 参考

+ `man xlsclients`
+ `man xdotool`
+ `man xwininfo`
