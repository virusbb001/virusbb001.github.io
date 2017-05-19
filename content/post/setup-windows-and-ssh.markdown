+++
categories = ["windows"]
date = "2017-05-07T17:53:32+09:00"
description = ""
keywords = []
title = "WindowsからSSH経由で開発するための環境セットアップ"

+++

Windowsで開発しようと思って良さそうなターミナルエミュレータがなかったので諦めて
VirtualBox内にArch Linux入れてSSHで開発できるようにした。

<!--more-->

# 初めに入れたもの

+ [Chocolatey](https://chocolatey.org/)
	+ Windowsパッケージマネージャ
+ [Bash on Ubuntu on Windows](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide)
+ [VirtualBox](https://www.virtualbox.org/)
+ [RLogin](http://nanno.dip.jp/softlib/man/rlogin/)
	+ かなり良さそうなssh等クライアント
	+ ローカルのシェルはサーバ立ち上げないと使えなさそう

# Chocolateyで入れたもの

+ fonts-ricty-diminished 4.1.0
	+ 定番フォント
+ nmap 7.40
+ openssh 0.0.12.0
+ ultravnc 1.2120
+ virtualbox 5.1.20
+ vcxsrv 1.19.2.0
	+ Xサーバ
	+ 原因不明だがEclipse使っていたらランチャーのサイズがおかしくなったので使っていない
+ MobaXTerm
	+ sshクライアント込だがXサーバとして使用

## 仮想マシン

VirtualBox上でArch Linuxをインストール

### ネットワーク設定

NATとホストオンリーアダプタを組み合わせる。
どちらもケーブル接続に設定。
仮想マシン側で [Arch Linux Wiki systemd-networkd#有線アダプタで固定IPを使用](https://wiki.archlinuxjp.org/index.php/Systemd-networkd#.E6.9C.89.E7.B7.9A.E3.82.A2.E3.83.80.E3.83.97.E3.82.BF.E3.81.A7.E5.9B.BA.E5.AE.9A_IP_.E3.82.92.E4.BD.BF.E7.94.A8)を参考に設定を行う。
Gatewayの設定は省略できる。

### X クリップボード

MobaXTermサーバではクリップボードに何か入れたければ `xclip -in` で入れることができる。
xselとかもあるのでそのあたりはお好みで。

