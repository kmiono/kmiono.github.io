# ターミナル改造記録

## 環境

OS：Windows 11 Home 22H2  
linux：Ubuntu 22.04.5 LTS  
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
> exa更新停止しているらしいので、ezaという似たコマンドをインストール  

### oh-my-bash の設定

導入に関しては公式参照

[oh-my-bash](https://ohmybash.nntoan.com)  

インストールコードは以下  
```
bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh)"
```
環境変数変えればテーマ変更できる。font（デフォルトテーマ）が設定されている環境変数を探して変更する。  

## 2023/08/01 追加分

主に以下のサイトを参考
[WSL2 + Windows Terminal + fish で快適な開発環境を構築しよう！（2023 年版）](https://qiita.com/irongineer/items/e5462d79bcaa903905b7)

インストール用コマンドは記事内または記事内リンクの公式サイトにて  
整理用に何を入れたのかを記述

### zip & unzip

コマンドライン上で zip を解凍したりするするコマンド  
ダウンロードに使う

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

#### Git 連携

以下の記事を参考  
[GitHub に ssh 接続できるようにする](https://qiita.com/0ta2/items/25c27d447378b13a1ac3)  

それでも`git push`が出来なかったため（commit はできた）

[GitHub 個人用アクセス トークン (PAT) 更新後の fatal: Authentication failed for エラー解消](https://zenn.dev/nasubita/articles/00f9ccb988e0a4)  
を参考に認証させる。

ちなみに Git Bash は SSH 接続するだけ（秘密鍵作るだけ）で接続できるっぽい
