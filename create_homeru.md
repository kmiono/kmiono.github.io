# Flutter でハビットトラッカーを作ってみた

## TD;TR

運動したら褒めてくれるアプリを作ろうと思いました。
ページ遷移 → 褒めてくれる → その回数を保存いう簡単な設計
スマホに入れて運動習慣付けるぞい！　という計画……だった。

### Flutter を入れる

[公式サイト](https://docs.flutter.dev/get-started/install)を見てください。  
要約すると「FlutterSDK を入れて環境変数通してね」なので（わかりづらいですが）簡単なはず。

### VSCode に拡張機能を入れる

- Dart
- Flutter
- Flutter Widget Snippets
- indent-rainbow

Dart と Flutter は言語パックなので必須  
Flutter Widget Snippets は補完機能なのであると楽  
indent-rainbow なしで Flutter 開発は無理ゲーです。入れましょう（ネストが深い）  
Prettier もあるといいと思うんですが、Flutter の整形は Prettier がやってるんじゃないっぽい？　ちょっとわからないです。

### プロジェクトを作る

ターミナルからコマンド打つのでもいいんですが、（というかそれが通常スタイルなんですが）、いちいちエクスプローラー立ち上げたりするの面倒なので、VSCode 内で完結させましょう。

1. VSCode を立ち上げたら、`ctrl+shift+p`を押します。
2. `flutter`と入力して、コマンドを絞り込みます。
3. `Flutter New Project`を選択してエンター
4. `Application`を選択してエンター
5. プロジェクトを作りたいフォルダを選択する画面が出てくるので、選んだら`Select a folder to create the project in`を押しましょう
6. プロジェクトが作られたら作業開始です

### MAIN.DART

`lib`配下の`main.dart`を以下のように編集します。

```
//上記変更なしのため記載なし

class _MyHomePageState extends State<MyHomePage> {

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("ほめるビットラッカー"),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            OutlinedButton(
              child: const Text(
                'ほめる',
                style: TextStyle(fontSize: 50),
              ),
              style: OutlinedButton.styleFrom(
                fixedSize: Size(250, 100),
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(10),
                ),
              ),
              onPressed: () => {
                Navigator.of(context)
                    .push(MaterialPageRoute(builder: (context) {
                  return HomeruPage();
                }))
              },
            ),
          ],
        ),
      ),
    );
  }
}

```

とりあえずボタン作ってページ遷移する所だけ作りました。  
遷移先がないので`HomeruPage()`にエラーが出ますが問題ないです。
