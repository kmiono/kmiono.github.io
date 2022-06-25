## GitKrakenのインストール

※GitHubのアカウントは既に取得している前提で進めます

[公式サイト](https://www.gitkraken.com/)からインストーラをダウンロード

![Image](install.png)

インストーラを起動して、以下の画面が開いたらとりあえず完了

![Image](gitkraken/install_finish.png)

## サインイン

![Image](gitkraken/sighup.png)

初期画面で「Sigh up wigh Github」を選択してクリック

ログインを求められるので、ユーザーネームとパスワードを入力

この画面に行ったら成功

「GitKrakenを開く」ボタンでGitKrakenを開き直す。

![Image](gitkraken/sighup_success.png)

開き直すと「ユーザーを作って」的な事を言われるが、

profile Name:GitHubのユーザー名

Author Name:GitHubのユーザー名

Author Email:GitHubに登録したアドレス

で問題ないと思います

アイコンは好きなの選びましょう。イーカーベーダーとか生き残ったイカの子とかNARUTOならぬIKATOとか名探偵イカチュウとか居ます。

設定すると画面どうする？　って聞かれるので素直にRepo Tab選びましょう。

Repo Tab選ぶと何か聞かれますが、有料機能を七日間トライアル（終わると無料モードに移行）なだけなので、黒い方のボタンを選びます(緑色のボタンは「仲間と一緒に始めよう」ってボタンらしいです)

## 初期設定

この状態でリポジトリをクローンしようとすると、「SSHキーがないよ！」と怒られるので、

![Image](toprofile.png)

ここから

SSHタブを押してこの画面にいきます。

![Image](ssh_generate.png)

四角で囲った部分を押すとsshキーを保存する画面が開くので、分かる場所（ドキュメントとか）に保存します。

「success!」の文字が出たら、

![Image](ssh_copy.png)

の四角に囲われた部分を押してキーをコピーします。

自分のGitHubを開いて、アカウントから「Settings」>「SSH and GPG keys」を開きます。

![Image](github_setting.png)

![Image](github_setting.png)

「New SSH key」ボタンを押すと次の画面に行くので、SSHキーの名前を入力して、先ほどコピーしたもの（ssh-rsa ～）を「key」の部分にペーストします。GitKrakenの操作してない限りはいつでもコピペし直せるので安心してください（この記事書く間に何度もコピペし直した人）。

![Image](key_add.png)

※流石にキーの中身は伏せてます。

これでGitHubとGitKrakenの連携が出来て、リポジトリがクローンできるようになりました。

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/kmiono/kmiono.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
