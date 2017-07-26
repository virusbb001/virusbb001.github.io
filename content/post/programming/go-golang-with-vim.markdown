+++
categories = ["programming", "Golang", "Vim"]
date = "2017-06-09T01:05:51+09:00"
description = "VimでGo言語触ってみたことの覚書"
keywords = []
title = "VimでGo言語を触ってみた"
draft = true

+++

Go言語を軽く触りました。敵情視察というわけではないですがGo言語について、
"ほら見てGolang wwwwwwww"しか言えないのはちょっとあれだなと思ったので以下に
簡単なやったこととか感想とかを殴り書きしようと思います。


<!--more-->

## 環境

+ Arch Linux
+ Go 1.8.3 linux/amd64
+ Vim 8.0 1-586

## Go言語と触れる

とりあえず触るだけ触ってみます。Go言語は[公式サイト](https://golang.org/#)から実際にコードを
動かすことができます。便利な時代ですね。

一通りサンプルを眺めて、勉強したくなったら[A Tour of Go(日本語)](https://go-tour-jp.appspot.com/welcome/1)
で言語の機能を一通り勉強することができます。

ある程度進めていくと(あるいは進めなくても)、[Vim](http://www.vim.org)が使いたくなってくると思います。
いい機会なのでGo言語開発環境とGo言語用のプラグインを入れます。

## Goをローカルに入れる

まずArch LinuxにGoを入れます。[Arch LinuxのWikiの日本語のGoのページ](https://wiki.archlinuxjp.org/index.php/Go)があるのでそれに従います。いい時代になりましたね。
今回は`pacman -S go`を行いました。

## Goのテスト兼Hello, 世界

`go`が正常に動作するかも兼ねて、実際にGo言語の動作確認を行います。

適当なディレクトリに以下のHello Worldプログラムを書きます。なお執筆時点でのVimには標準でGo言語のシンタックスファイルが有るようです。

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, World!")
}
```

`:w hello.go`したあと、`:!go run`をします。
`Hello, World!`と出てきたらGoは正常に動作しています。これでGo言語を使って仕事をしているときに"この実行結果を見てgo run wwwwwww"と言うことができるようになりました。やりましたね。

また、コンパイルも正常に動作するかを確認します。
`:q`したあと、`go build hello.go` を行いビルドします。実行ファイル(執筆時点では`hello`)ができていることを確認し、実行して`go run`した時と同じ結果が出るかを確認します。

## VimでGoを書く

Go言語は[GithubのWikiにIDEやエディタのプラグインをまとめたページ](https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins)があります。
[fatih/vim-go](https://github.com/fatih/vim-go)プラグインを入れます。
私は[Shougo/dein.vim](https://github.com/Shougo/dein.vim)を使用し、tomlで管理しているので以下の設定を追記しました。

```
[[plugins]]
repo = 'fatih/vim-go'
on_ft = 'go'
lazy = 1
```

インストール後、fatih/vim-goのREADMEのInstallの項目に従い、`:GoInstallBinaries`を行います。
あとはvim-goがやってくれますが、時間がかかるので待ちます。

## vim-goに慣れる

vim-goは実際機能が豊富ですが、vim-goには[fatih/vim-go-tutorial](https://github.com/fatih/vim-go-tutorial#documentation-lookup)というオフィシャルチュートリアルがあるので、それをやると一通りの機能に触れることができます。

## Go言語に慣れる

実際のGo言語の勉強に見たページです。

+ [A Tour of Go(日本語)](https://go-tour-jp.appspot.com/welcome/1)
	+ [原文](https://tour.golang.org/welcome/1)
+ [Effective Go(日本語)](http://go.shibu.jp/effective_go.html)
	+ [原文](https://golang.org/doc/effective_go.html)
+ 実際のGoライブラルのソース
	+ `go env GOROOT`のsrcにライブラリ等のソースが入っています。
+ [はじめてのGo―シンプルな言語仕様，型システム，並行処理](http://gihyo.jp/dev/feature/01/go_4beginners)

TODO: もう少し調べて追記する
