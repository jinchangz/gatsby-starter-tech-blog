---
title: 'Windows10のWSL(Windows Subsystem Linux)にGatsbyをインストール'
date: '2018-12-08'
tags: ['JavaScript', 'Gatsby']
---

##  概要

windows10の環境にて静的サイトジェネレータの一種であるGatsbyをインストールするまでを記事にしてみます。

Gatsbyには以下のような特徴があります。

### 静的なコンテンツを生成、構築、配信

世界中に配布されているCDNにキャッシュされ、サーバーレスでデプロイできる「静的な」ファイルとして構築します。

### リンク先ページの先読み込み

Gatsbyは、すぐにコンテンツの事前読み込みをサポートします。つまり、ページが読み込まれると、次にクリックしたリンクを読み込むために必要なコンテンツは、ページを閲覧している間バックグラウンドで読み込まれます。

### サーバーレスでサイト運用

サーバーレスとは、セキュリティやフレームワークのアップグレードについて心配する必要がないということです。これは運用時間の短縮を意味します - 運用中のサーバーにSSHで接続して何が起こっているのかを確認する必要はありません。



まだまだGatsbyには機能があるのですが個人で導入する場合は

運用するのがレスポンス、セキュリティ、メンテナンス、コストなどの面で非常にパフォーマンが優れております。

当サイトではGatsbyの情報を主にコンテンツとして配信していきます。

## 開発環境＆対象読者

### 対象読者

Windows10ユーザーの方でHTML,CSS,Javascriptの基本的な知識がある人が対象です。あとBashというUnixやLinuxで広く使われているWindowsでいうコマンドプロンプトを使ってのファイル操作を行います。なのでMacやLinuxをお使いの方はやることはほぼ同じです。基本的に初級者向けの解説を心掛けたいのでJavascriptとBashのほうはなるべく丁寧に解説していきます。

### 開発環境

#### windows10

言わずもがな、最新の安定バージョンにしてください。

#### WSL(Ubuntu18.04)

Windows Subsystem for Linux(以下WSL)にLinuxのディストリビューションで人気のあるUbuntu18.04を使用して開発していきます。

#### WSLtty

wslttyとWSL標準のコンソールより高機能な端末を使用します。以下のような機能があります。

- より高速で高機能、高度な端末エミュレーションの実現
- ズーム機能（マウスホイールによるや拡大／縮小）やキーボードによるスクロール（［Shift］＋［Page Up］／［Page Down］）、1万行を超えるバッファリングなど
- 容易なウィンドウの新規オープン（［Alt］＋［F2］）や切り替え（［Ctrl］＋［Shift］＋［Tab］）
- 設定（ファイル）の保存や起動時の適用
- Windows OSのエクスプローラーからドラッグ＆ドロップしたファイルやフォルダのパス名を、自動的にWSL向けのパスに変換して貼り付け可能（例：「c:\doc\file1.txt」を「/mnt/c/doc/file.txt」にする）

### 事前環境のインストール

#### WSL
こちらを参考にしてください。 

[WSLのインストール](/2018-12-07-WSLのインストール/)




#### WSLtty

## インストール手順

### WSLをアップグレード

まずはインストールしたWSLのアップグレードを行います。

WSLttyを起動して以下のコマンドを入力実行してください。

しばらく時間がかかるので気長に待ちましょう。

```shell:title=bash
sudo apt update
sudo apt -y upgrade
```

### ビルドツールをインストール

Gatsby公式ではnpmのビルドツールである`node-gyp`もインストールが必要かもしれないとのことなのであとでインストールします。

```shell:title=bash
sudo apt install -y build-essential
```

### nodejsをアンインストール＆インストール

nodejs公式からのインストール手順では少々エラーが残るとのことなので代わりに

Ubuntuに標準でインストールされているnodejsをアンインストールして新たにn-installというnodejsバージョン管理ツールをインストールします。バージョン管理についてはnodenvなどのほうが私的には使いやすいのですがここではGatsby公式サイトのやり方に従います。

```shell:title=bash
sudo apt remove nodejs
curl -L https://git.io/n-install | bash
exec $SHELL -l
```

最後の`exec $SHELL -l`でshellを再起動します。

### node-gypをインストール
必要かどうかわかりませんが一応インストールしておきます。

`-g`のオプションでグローバル環境でインストールしましょう。

```shell:title=bash
npm install -g node-gyp
```



### Yarnをインストール

Gatsby公式サイトではnpmというjavascriptパッケージマネージャーを使用して解説しておりますが当サイトではYarnというパッケージマネージャーをしようして行きたいと思います。

Yarnについてはこちらの解説がわかりやすかったです。

[npmから乗り換えてわかったYarnの4つのメリット - ICS MEDIA](https://ics.media/entry/19384)

[Yarnとnpmの違い：JavaScriptパッケージマネジャーを比較する - WPJ](https://www.webprofessional.jp/yarn-vs-npm/)

それでは公式サイトのやり方に則ってインストールします。

```shell:title=bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

```



### gatsby-cliをインストール

## まとめ

### コマンド一覧



### 



