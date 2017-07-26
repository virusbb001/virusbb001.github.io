+++
categories = ["Linux", "Gentoo"]
date = "2017-07-26T22:42:45+09:00"
description = ""
keywords = []
title = "#GentooInstallBattle を終えてカーネルの設定いじってインストールし直したら起動しなくて焦った話"

+++

表題のとおりです。

<!-- more -->

# 環境

+ VirtualBox 5.1.24
+ Gentoo Linux
	+ EFI有効化
	```
	cat /etc/gentoo-release
	Gentoo Base System release 2.3
	uname -r
	4.9.34-gentoo
	```

# 手順

1. #GentooInstallBattle を終える
2. [GentooWikiのVirtualBoxの記事](https://wiki.gentoo.org/wiki/VirtualBox#Gentoo_guests)を見ながらカーネルの設定を変更・インストール
3. `make && make install`
	+ `/boot`がマウントされていることは確認済み
4. 再起動する
5. grubでカーネル選択後、`echo 'Loading Linux 4.9.34-gentoo'`の後が止まる
6. 焦る
7. 何を思ったか別の仮想マシンを作成してGentooをインストールし直す
8. 新しいGentooの/bootから古いGentooのディスクイメージをrootにして起動するよう設定
9. うまくいくことを確認
	+ だめだったらまたその時の記事を書く
10. `/boot`が原因であることを推測する
11. 新しいGentooを通常通り起動し、`/boot`を`unount`, 古いGentooの`/boot`に置き換える
12. 新しいGentooで`cd /usr/src/linux; make install`する
13. `grub-mkconfig -o /boot/grub/grub.cfg`
14. 新しいGentooを`shutdown -h now`
15. 古いGentooを起動
16. `cd /usr/src/linux`
17. `cp /boot/config-4.9.34-gentoo config.succeed`
18. `make menuconfig`
19. `Load`して`config.succeed`
	+ 最初これをやらなかったのが原因かも？
20. `make && make install`
21. `reboot`して動作を確認

