# ターミナル改造記録

## 環境

OS：Windows 11 Home 22H2  
linux：Ubuntu 20.04.5 LTS  
ターミナル：Tabby Terminal（Windows Terminal が使いづらいため代替）

## やったこと

- 拡張コマンドの追加
- oh-my-bashの追加

## 入れたもの

- zip & unzip
- fzf
- ghq
- z

### 拡張コマンドの追加

- fd
- exa
- fzf
- ghq
  コマンドを追加

コマンドについては下記より

[もっと使いやすいコマンドラインツール 10 選](https://zenn.dev/the_exile/articles/5176b7a5c29bce#4.-fd%EF%BC%88find%EF%BC%89)  
[fzf を活用して Terminal の作業効率を高める](https://qiita.com/kamykn/items/aa9920f07487559c0c7e)  
[fzf と ghq を組み合わせてプログラミングの心理的・作業的負荷を軽減する](https://zenn.dev/isana/articles/20210628fzfghq)

> [!warning]
> 2024/04/16対応  
> homebrewがexa非対応になった？　exaがhomebrew非対応になった？　のでezaという似たコマンドをインストール  

### oh-my-bash の設定

導入に関しては公式参照

[oh-my-bash](https://ohmybash.nntoan.com)  

インストールコードは以下  
```
bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh)"
```
環境変数変えればテーマ変更できるらしいが出来てない。要調査。  

## 2023/08/01 追加分

主に以下のサイトを参考
[WSL2 + Windows Terminal + fish で快適な開発環境を構築しよう！（2023 年版）](https://qiita.com/irongineer/items/e5462d79bcaa903905b7)

インストール用コマンドは記事内または記事内リンクの公式サイトにて  
整理用に何を入れたのかを記述

### zip & unzip

コマンドライン上で zip を解凍したりするするコマンド  
ダウンロードに使う

### fish

今回は無事起動。brew コマンドも無事動いた。  
恐らく前回は再起動をしていなかったため動かなかったのではないかと推測。

### Fisher

fish のプラグインマネージャ  
旧 Fisherman。古い記事だと Fisherman の記述を見かける。

### asdf

バージョン管理ツールらしい

```
asdf とは 開発言語（Node.js、Python など）や開発ツール（AWS CLI, AWS SAM CLI, Terraform など）のバージョンを管理できるコマンドラインツールです。
```

とのこと。

多分入れていて損はないはず。

### fzf

フィジーファインダー(fuzzy finder)なので fzf

```
fzf #fzf起動
[ファイル名]
```

すれば検索ができる。素晴らしい。  
peco という似た存在（コマンド）がいるらしい。

### ghq

由来はたぶん GitHub Qlone(Clone)  
いわく

```
ghq は、GitHub やその他のリモートリポジトリのローカルクローンを整理し管理するためのツール
```

### z

```
過去にアクセスしたディレクトリを追跡します。
頻度と最新性を組み合わせて、念頭に置いたディレクトリにジャンプできます。
cd コマンドの履歴から指定された相対パスに部分一致するパスを検索しています。
z をインストールした後にアクセスしたことあるディレクトリにしか行けません。
Tab での補完もできます。
```

とのこと。  
なんならベストオブ把握できてないヤツまである。  
多分入れているだけで効果がある。

ちなみに動作確認はこんな感じ

```
$ cd ~/.config/fish/ # 移動したいディレクトリへアクセス
$ cd ~ # 動作確認のため、他の適当なディレクトリへ移動
$ cd fish # ~/.config/fish/ へ移動できる
```

### fish-bd

ディレクトリを上に遡れる。そんだけ

```
bd # cd ..
```

って入れるだけで爆速で上に行くので結構便利。補完が利くので bd を入れるだけでよいのがなお便利

### 起動時に fish ロゴを表示

fish_logo という魚を表示するプラグインを利用して起動時に魚を表示させるようにする。  
これにより何のシェルを使っているのか分かりやすくなる。

上記[bash への切り替え](#bashへの切り替え)にて戻せる。

### oh-my-fish の設定

oh-my-fish：fish のカラーテーマ  
今回は bobthefith を採用  
ちなみに powershell 用の oh-my-posh とか bash 用の oh-my-bash とか色々いる

### AstroNvim の追加

主に[VSCode が物足りない人へ AstroNvim の紹介](https://zenn.dev/chot/articles/72bc7dfbec3b33)を参照

plugin ファイルは~/.config/nvim/lua/plugins 以下にある。
クリップボードへコピーが出来るので良い（vim はその辺の処理がまた特殊なので設定をいじくる必要あり）。

#### Git 連携

以下の記事を参考  
[GitHub に ssh 接続できるようにする](https://qiita.com/0ta2/items/25c27d447378b13a1ac3)  
ただし fish shell にしているため

```
eval "$(ssh-agent -s)"
```

コマンドは動かない

```
eval (ssh-agent -c)
```

を使う

それでも`git push`が出来なかったため（commit はできた）

[GitHub 個人用アクセス トークン (PAT) 更新後の fatal: Authentication failed for エラー解消](https://zenn.dev/nasubita/articles/00f9ccb988e0a4)  
を参考に認証させる。

ちなみに Git Bash は SSH 接続するだけ（秘密鍵作るだけ）で接続できるっぽい
