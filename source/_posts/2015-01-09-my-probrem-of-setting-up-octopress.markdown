---
layout: post
title: "Octopressのセットアップのメモ"
date: 2015-01-09 17:53:51 +0900
comments: true
categories: 
---

セットアップには[OctopressでGitHub無料ブログ構築。sourceをBitbucket管理。簡単ガイド！ - 酒と泪とRubyとRailsと](http://morizyun.github.io/blog/octopress-gitpage-minimum-install-guide/)と[Octopress公式のドキュメント](http://octopress.org/docs/setup/)を参考にしました．  
正直にいってここさえ見てしまえばだいたいなんとかなります．  

ただこの通りにやっても404になったりとかがあったのでその時のメモを下に書いておきます．  
まず，リポジトリ名があっているかの確認です．  

1. [GitHub](https://github.com)からリポジトリ`username.github.io`にいきます
2. そこのSettingsをクリックします
3. GitHub Pagesあたりまでスクロールします
4. Your site is published at なんちゃらって出てきたら多分大丈夫です

この時masterにファイルが有ることを確認します．他のブランチだと表示されません．  
すぐに`http://username.github.io/`にアクセスしても404になっている時があります．  
ここで先ほどのリポジトリの設定のGitHub Pagesあたりをもう一度見てみましょう．  

> Changes may take up to 30 minutes to be visible.

らしいので30分ぐらいゲームでもして待っていましょう．そうすると反映されているはずです．  

自分が直面した問題はこのくらいです．  

追記: TOEIC IPの試験が明日ありますが全く勉強していません．実際ヤバイです．
