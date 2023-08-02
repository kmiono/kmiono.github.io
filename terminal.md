# ターミナル改造記録

## 環境

OS：Windows 11 Home 22H2  
linux：Ubuntu 20.04.5 LTS  
ターミナル：Tabby Terminal（Windows Terminal が使いづらいため代替）

## やったこと

- homebrew のインストール
- fish shell のインストール
- bash への切り替え
- 拡張コマンドの追加
- starship の設定

## 2023/08/01 追加分

## 入れたもの

- zip & unzip
- fish shell
- Fisher
- asdf
- oh-my-fish
- fzf
- ghq
- z
- fish-bd
- 起動時に fish ロゴを表示

### homebrew のインストール

以前公式通りにやって失敗したので、下記記事を参照しました。

[WSL+homebrew+fish 環境構築まとめ](https://qiita.com/m0710fa/items/fb231eadef55d69b4450)

このとき`/etc/shells`に追加した設定

```
/home/linuxbrew/.linuxbrew/bin/fish
/usr/local/bin/fish
/opt/homebrew/bin/fish
```

### fish shell のインストール

~~上記「WSL+homebrew+fish 環境構築まとめ」を参照してインストール。~~  
~~しかし~~

- ~~入れたはずの brew コマンドが効いてくれない~~
- ~~fish のメジャーパッケージ管理ツールを使っても拡張コマンドが追加できない~~
- ~~原因を調べようにも時間がかかりすぎる~~
  ~~などの理由からおよそ 2 時間で bash へ戻すことになりました。~~

~~補完が非常に有能なので linux の知見が集まったらまた挑戦したいと思います。~~  
~~（諸々のパスが引き継がれていなかった気がする）~~

下記[fish](#fish)にて実装

### bash への切り替え

`/etc/shells`から fish のログインシェルに関係する`/usr/local/bin/fish`を削除

下記コマンドを実行して再起動  
（コマンドだけで良い気はする）

```
chsh -s /bin/bash
```

### 拡張コマンドの追加

bash に戻したところ`brew`コマンドが使用できたので、

- fd
- exa
- fzf
- ghq
  コマンドを追加

コマンドについては下記より

[もっと使いやすいコマンドラインツール 10 選](https://zenn.dev/the_exile/articles/5176b7a5c29bce#4.-fd%EF%BC%88find%EF%BC%89)  
[fzf を活用して Terminal の作業効率を高める](https://qiita.com/kamykn/items/aa9920f07487559c0c7e)  
[fzf と ghq を組み合わせてプログラミングの心理的・作業的負荷を軽減する](https://zenn.dev/isana/articles/20210628fzfghq)

### starship の設定

導入に関しては下記

[Rust 製ツールでおしゃれなターミナル環境を作る【Starship ✕ exa】](https://zenn.dev/ryuu/articles/customize-your-terminal)

```
starship config
```

を入力して設定を表示、編集

※:wq コマンドで設定ファイルを保存できない(readonly)設定の時は下記参照

[WSL2 で Starship を使っておしゃれなターミナルを作成する](https://qiita.com/Sicut_study/items/6aa87a758132ca006d5)

現状の設定

```
add_newline = true

# タイムアウト時間
scan_timeout = 10

[character]
success_symbol = "[▶](bold green)" # コマンド成功時
error_symbol = "[▶](bold red)"    # コマンド失敗時
vicmd_symbol = "[◀](bold green)"

[cmd_duration]
format = " [$duration]($style)"

[directory]
read_only = " "
truncate_to_repo = false
truncation_symbol = " /"

[git_status]
disabled = true

[memory_usage]
disabled = false
format = "via [$symbol$ram_pct]($style) "
symbol = " "

[time]
disabled = false
format = "[$time]($style) "
use_12hr = true

[aws]
symbol = "  "

[conda]
symbol = " "

[dart]
symbol = " "

[docker_context]
symbol = " "

[elixir]
symbol = " "

[elm]
symbol = " "

[git_branch]
symbol = " "

[golang]
symbol = " "

[hg_branch]
symbol = " "

[java]
symbol = " "

[julia]
symbol = " "

[nim]
symbol = " "

[nix_shell]
symbol = " "

[package]
symbol = " "

[perl]
symbol = " "

[php]
symbol = " "

[python]
symbol = " "

[ruby]
symbol = " "

[rust]
symbol = " "

[scala]
symbol = " "

[swift]
symbol = "ﯣ "
```

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
