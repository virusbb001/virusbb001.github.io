---
layout: post
title: "MinecraftのJarに直接ぶち込む形式のModの導入方法"
date: 2015-01-19 07:28:39 +0900
comments: true
categories: [minecraft]
---

備忘録  
だいたいは[まいんくらふとにっき](http://ghasts.blog.fc2.com/blog-entry-571.html)を参考に  
jarファイルでないと実行してくれない模様  

<!-- more -->

1. 入れたいバージョンのMinecraft本体をダウンロード
2. 入れたいバージョンのMinecraftをコピー
3. 欲しいバージョンのForgeをダウンロード
4. Forgeの展開  
	+ 展開する前にディレクトリを作成してその中で行う
	+ 展開のコマンド: `unzip filename`
5. Minecraft本体の展開
	+ 新しくディレクトリを作る
	+ `jar xf 本体.jar`
6. Minecraft本体のMETA-INF削除
	+ `rm -rf META-INF`
7. Forgeをインストール
	+ `cp -R forge展開先/* minecraft展開先`
8. 圧縮
	+ `jar cf 本体.jar -C 展開先/ .`
	+ 圧縮しないとダウンロードしに行こうとする
9. 確認
	+ ランチャーを起動してプロファイルの設定をする
	+ 設定したらMinecraftを起動
	+ 右下にForgeとか出てきたら成功です
