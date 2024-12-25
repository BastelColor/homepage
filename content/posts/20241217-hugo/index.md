---
title: "Hugoめちゃ便利"
summary: "このサイトの作り方など"
date: 2024-12-11
coverCaption: "かわいいです"
keywords: "謎"
showTableOfContents: true
showSummary: true


description: "HTMLメタデータです"

---

## この記事について
この記事は[KCS Advent Calendar 2024](URL "https://qiita.com/advent-calendar/2024/kcs/")に枠が余っていたら入れる予定だった記事です。

## サイト作りたい！
なんとなくサイトが作りたくなったので、色々と調べてました。KCSでアドバイスとかもらいつつ、やっぱりコードとかよくわからねぇなといった感じ。

そこで、逆にテンプレートが配布されてるやつから逆算して、サイトの作り方を決めようとしました。そこで見つけたのが[Hugo]({{< ref "https://gohugo.io/" >}})です。

![Hugo](img/hugo.jpeg "めっちゃ便利")

## とりあえずセットアップ
セットアップ方法については各OSごとに異なる。注意点としては、ただのHugoじゃなくてHugo Extendedというバージョンをインストールする必要あり。
詳しいインストール方法については[ここ](URL "https://gohugo.io/installation/")で見れるのでOSに合わせて各自入れてください。

次に、ディレクトリの作成を行います。作り方は簡単で、

``` 
hugo new site homepage 
```

これだけでいけます。`homepage`の部分については作りたいフォルダ名に応じて変更してください。

Hugoはプリセットというかテーマが有志から配布されています。今後github pagesを使っていくことも考えて、gitのセットアップも行いましょう。なので、

```
cd homepage
git init
```
これだけやっておけばOKです。また、githubにアップロードする必要もあるので、

```
git add .
git commit -m "initialize"
git remote add origin https://github.com/<username>/<repo-name>.git
git push origin master
```

こんな感じでいいと思います。VSCodeを使っている場合は拡張機能を使ったほうがいくらか便利です。

さて、このサイトのテーマについては[Congo](URL "https://github.com/jpanther/congo")というテーマを使っています。色々と試して、これに行きつきました。

![Congo](img/screenshot.png "簡単にイマドキなサイトが作れるテーマ")

テーマについてはgitのsubmoduleというものを使って入れます。本当のところ何も分かってないですが、多分自動でアップデートとかできるんだと思います。あとは、別のリポジトリとして管理できるとかそんなところ。

Congoテーマのインストールは以下のコマンドです。

```
hugo mod init github.com/<username>/<repo-name>
```

これに加えて、`config/_default/module.toml`に

```
[[imports]]
path = "github.com/jpanther/congo/v2"
```
と書いてください。

最後に、
```
hugo server
```
を実行することで、ローカルホスト上でウェブサーバーが立ちます。初回起動時に、importsの設定に応じて必要なファイルのセットアップも自動でやってくれるのでまずは起動しましょう。

これだけでサイトとしてのセットアップは完了です。

## 他にやること

github pagesを使う場合、docsフォルダをページ用のディレクトリに設定しておいた方が何かと便利です。なので、`<directory>/hugo.toml`に
```
publishDir = "docs"
```
と書き込んでおきましょう。これで、hugo server時に生成されるhtmlファイルその他が`<directory>/docs/`以下に出力されます。

また、言語設定については自分で作るようになっています。初期設定では英語なので、日本語にするには`config/`下に`languages.ja.toml`を作成、適宜内容を記述する必要があります。

これらの設定については公式ドキュメントがそこそこ分かりやすいので、[こちら](URL "https://jpanther.github.io/congo/docs/")を参照してください。

## 最後に
ホームページ作りは結構ハードル高いですが、今となっては色々と便利なツールが出ているのでぜひ挑戦してみてください。