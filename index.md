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

アイコンは好きなの選びましょう。イーカーベーダーとかイカ残った男の子とかNARUTOならぬIKATOとか名探偵イカチュウとか居ます。

設定すると画面どうする？　って聞かれるので素直にRepo Tab選びましょう。

Repo Tab選ぶと何か聞かれますが、有料機能を七日間トライアル（終わると無料モードに移行）なだけなので、黒い方のボタンを選びます(緑色のボタンは「仲間と一緒に始めよう」ってボタンらしいです)

## 初期設定

この状態でリポジトリをクローンしようとすると、「SSHキーがないよ！」と怒られるので、

![Image](gitkraken/toprofile.png)

ここから

SSHタブを押してこの画面にいきます。

![Image](gitkraken/ssh_generate.png)

四角で囲った部分を押すとsshキーを保存する画面が開くので、分かる場所（ドキュメントとか）に保存します。

「success!」の文字が出たら、

![Image](gitkraken/ssh_copy.png)

の四角に囲われた部分を押してキーをコピーします。

自分のGitHubを開いて、アカウントから「Settings」>「SSH and GPG keys」を開きます。

![Image](gitkraken/github_setting.png)

![Image](gitkraken/github_sshkey.png)

「New SSH key」ボタンを押すと次の画面に行くので、SSHキーの名前を入力して、先ほどコピーしたもの（ssh-rsa ～）を「key」の部分にペーストします。GitKrakenの操作してない限りはいつでもコピペし直せるので安心してください（この記事書く間に何度もコピペし直した人）。

![Image](gitkraken/key_add.png)

※流石にキーの中身は伏せてます。

これでGitHubとGitKrakenの連携が出来て、リポジトリがクローンできるようになりました。

## クローン

GitKrakenの画面の「Clone a repo」を押します。

![Image](gitkraken/clone_repo.png)

分かる場所に空ファイルを作っておいて、Browseで作った空ファイルを選択します。

※GitKrakenがフォルダ作ってくれるので、デスクトップ選択、Cドライブ選択でも大丈夫です。

![Image](gitkraken/dir_brows.png)

GitHubでクローンしたいリポジトリの「code」ボタン>SSHタブに現れるurlをコピーします。

![Image](gitkraken/compass_rep.png)

GitKrakenのURLにペーストすると以下の画面になるので

![Image](gitkraken/clone_repo_coped.png)

「Clone the repo!」ボタンを押します

こんなメッセージが出てきたら「Open now!」を押しましょう。

![Image](gitkraken/open_q.png)

おめでとうございます、リポジトリがクローンできました！

![Image](gitkraken/clone_repo_success.png)
