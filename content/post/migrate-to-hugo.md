+++
categories = []
date = "2017-05-03T00:02:50+09:00"
description = ""
keywords = []
title = "hugoに移行しました"

+++

手順は基本的に [hugo import jekyll](https://gohugo.io/commands/hugo_import_jekyll/) に従う。  
URLを無視するならこれで問題ないはずだけど、個人的にはURLは変わってほしくなかったので追加の手順が必要。  

<!--more-->

以下のコマンドを実行した。`hugo server` 実行中なら止めてからやったほうが良さそう？

1. permalinkの設定  
	octopressのconfigのpermalinkの設定を `/blog/:year/:month/:day/:title/` にしていたため、
	`config.yaml` 内の`permalinks`の設定を`post: /blog/:year/:month/:day/:filename/`を追加  
	filenameなのはOctopressだった頃のファイル名を `YYYY-MM-DD-TITLE.markdown`にしたためと、 `:title` を使用すると表示用のタイトルがURLに含まれてしまうため。
2. ファイル名の変更  
	前述の通り、ファイル名に年月日が含まれているので取り除く。  
	[システム開発メモ 正規表現やワイルドカードでファイル名を一括変換する](http://progmemo.wp.xdomain.jp/archives/813)を参考に，  
	`\ls -1 | grep -E "^[0-9]{4}" | xargs -I % echo -e '%\n%' | sed -r '2~2s:^[0-9]{4}-[0-9]{2}-[0-9]{2}-(.*)$:\1:g' | xargs -n 2 mv`を実行。  
	grep噛ませているのはすでに作成された記事対策のため。  
3. urlの設定を消す  
	`sed -e '/^url:/d' -i.bak *`  
	中身確認して問題なければ`rm *.bak`  
