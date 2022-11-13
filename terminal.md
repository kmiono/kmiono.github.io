# ターミナル改造記録

## 環境

OS：Windows 11 Home 22H2  
linux：Ubuntu 20.04.5 LTS  
ターミナル：Tabby Terminal（Windows Terminalが使いづらいため代替）  

## やったこと

- homebrewのインストール
- fish shellのインストール
- bashへの切り替え
- 拡張コマンドの追加
- starshipの設定

### homebrewのインストール

以前公式通りにやって失敗したので、下記記事を参照しました。

[WSL+homebrew+fish環境構築まとめ](https://qiita.com/m0710fa/items/fb231eadef55d69b4450)

このとき`/etc/shells`に追加した設定

```
/home/linuxbrew/.linuxbrew/bin/fish
/usr/local/bin/fish
/opt/homebrew/bin/fish
```

### fish shellのインストール

上記「WSL+homebrew+fish環境構築まとめ」を参照してインストール。  
しかし  
- 入れたはずのbrewコマンドが効いてくれない
- fishのメジャーパッケージ管理ツールを使っても拡張コマンドが追加できない
- 原因を調べようにも時間がかかりすぎる
などの理由からおよそ2時間でbashへ戻すことになりました。

補完が非常に有能なのでlinuxの知見が集まったらまた挑戦したいと思います。  
（諸々のパスが引き継がれていなかった気がする）

### bashへの切り替え

`/etc/shells`からfishのログインシェルに関係する`/usr/local/bin/fish`を削除

下記コマンドを実行して再起動  
（コマンドだけで良い気はする）

```
chsh -s /bin/bash
```

### 拡張コマンドの追加

bashに戻したところ`brew`コマンドが使用できたので、
- fd
- exa
- fzf
- ghq
コマンドを追加

コマンドについては下記より

[もっと使いやすいコマンドラインツール10選](https://zenn.dev/the_exile/articles/5176b7a5c29bce#4.-fd%EF%BC%88find%EF%BC%89)  
[fzfを活用してTerminalの作業効率を高める](https://qiita.com/kamykn/items/aa9920f07487559c0c7e)  
[fzfとghqを組み合わせてプログラミングの心理的・作業的負荷を軽減する](https://zenn.dev/isana/articles/20210628fzfghq)

### starshipの設定

導入に関しては下記

[Rust製ツールでおしゃれなターミナル環境を作る【Starship ✕ exa】](https://zenn.dev/ryuu/articles/customize-your-terminal)

```
starship config
```
を入力して設定を表示、編集

※:wqコマンドで設定ファイルを保存できない(readonly)設定の時は下記参照

[WSL2でStarshipを使っておしゃれなターミナルを作成する](https://qiita.com/Sicut_study/items/6aa87a758132ca006d5)

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

