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
基本的に Flutter は`lib`配下のファイルを編集します。

`main.dart`

```
//ここより上変更なしのため記載なし

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

### HomeruPage を作る

あまりに安直ネームですが、わかりやすい方がいいんです（多分）

`lib`配下に新規に`homeru_page.dart`を作成します。

`homeru_page.dart`

```
import 'package:flutter/material.dart';

class HomeruPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("ほめるページ"),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            OutlinedButton(
              child: const Text(
                '戻る',
                style: TextStyle(fontSize: 50),
              ),
              style: OutlinedButton.styleFrom(
                fixedSize: Size(250, 100),
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(10),
                ),
              ),
              onPressed: () => {Navigator.of(context).pop()},
            )
          ],
        ),
      ),
    );
  }
}

```

まだ画面遷移できませんし、画像も表示されません。

```
import 'dart:math';

import 'package:flutter/material.dart';
//追加
import 'homeru_page.dart';

//ここより上変更なしのため記載なし

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

これで画面遷移は出来るようになりました。

### 画像の表示

表示したい画像を image フォルダに追加し（フォルダがなかったら作成）、
pubspec.yaml の末尾に以下を追加します。
`homeru_page.dart`を

```
  assets:
    - images/1000_F_481094487_KgEvOuZZmm1PLbPPSzGf7MEJrNtPFpgN.jpg
    //この画像はネットで適当に拾ってきたやつです
```

`images/1000_F_481094487_KgEvOuZZmm1PLbPPSzGf7MEJrNtPFpgN.jpg`を以下のように修正します。

```
import 'package:flutter/material.dart';

class HomeruPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("ほめるページ"),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Image.asset('images/1000_F_481094487_KgEvOuZZmm1PLbPPSzGf7MEJrNtPFpgN.jpg'),//表示したい画像の名前を入れる
            OutlinedButton(
              child: const Text(
                '戻る',
                style: TextStyle(fontSize: 50),
              ),
              style: OutlinedButton.styleFrom(
                fixedSize: Size(250, 100),
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(10),
                ),
              ),
              onPressed: () => {Navigator.of(context).pop()},
            )
          ],
        ),
      ),
    );
  }
}

```

画像が表示されました。

#### サイズを変更したいとき

`Container()`で囲むといいらしいです

```
Container(
                color: Colors.indigo, // To see the difference between the image's original size and the frame
                height: 550,
                width: 300,

                // Uploading the Image from Assets
                child: Image.asset(
                  'images/pexels.jpg',//表示したい画像

                  // Resizing the Image to the Frame Size
                  fit: BoxFit.cover,
                ))

)
```

参考：[How To Resize Images in Flutter](https://img.ly/blog/how-to-resize-images-in-flutter/)2023/03/26 参照

### カウント機能の追加

`main.dart`を以下のように編集します。

```
import 'dart:math';

import 'package:flutter/material.dart';
//追加
import 'homeru_page.dart';

//以下変更なしのため記載なし

//以上変更なしのため記載なし

  class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  //追加
  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }


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
            //追加
            const Text("頑張った回数:"),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headlineMedium,
            ),
            //追加ここまで
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

褒めるボタンを押すたびにカウントがされるようになりました。
でも画面を消すとカウントがリセットされるので、保存機能を付けたいと思います。

### 保存機能の追加

ローカルに保存するため shared_preferences を使います。

1. まず ctrl+`で VSCode 内のターミナルを呼び出します。
2. `flutter pub add shared_preferences`と入力します
3. `pubspec.yaml`に

```
dependencies:
  shared_preferences: ^2.0.20
```

が追加されていれば大丈夫です

4. `main.dart`を以下のように修正します

```
import 'dart:math';

import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';//追加
import 'homeru_page.dart';

//以下変更なしのため記載なし

//以上変更なしのため記載なし

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
      //追加
      _setPrefItems(); // Shared Preferenceに値を保存する。
    });
  }

//追加

  // Shared Preferenceに値を保存されているデータを読み込んで_counterにセットする。
  _getPrefItems() async {
    SharedPreferences pref = await SharedPreferences.getInstance();
    setState(() {
      // 以下の「counter」がキー名。見つからなければ０を返す
      _counter = pref.getInt('counter') ?? 0;
    });
  }

  // Shared Preferenceにデータを書き込む
  _setPrefItems() async {
    SharedPreferences pref = await SharedPreferences.getInstance();
    // 以下の「counter」がキー名。
    pref.setInt('counter', _counter);
  }

  @override
  void initState() {
    super.initState();
    // 初期化時にShared Preferencesに保存している値を読み込む
    _getPrefItems();
  }

//追加ここまで

  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("ほめるビットラッカー"),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text("頑張った回数:"),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headlineMedium,
            ),
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
                _incrementCounter(),
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

画面を閉じてもカウンターの値が保存されるようになりました。

参考：[ブラウザで Flutter! - 保存してみよう！](https://note.com/dngri/n/na4c9e7e7b0e6)

### デザイン修正

戻るボタンがいけてないので修正しようと思います。
ライブ感で作ってるからこういうことが起きる……。

調べたところ実装してたボタン削除するだけでいいみたいです。便利。

```
import 'package:flutter/material.dart';

class HomeruPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("ほめるページ"),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Image.asset('images/1000_F_481094487_KgEvOuZZmm1PLbPPSzGf7MEJrNtPFpgN.jpg'),//表示したい画像の名前を入れる

            //削除
            OutlinedButton(
              child: const Text(
                '戻る',
                style: TextStyle(fontSize: 50),
              ),
              style: OutlinedButton.styleFrom(
                fixedSize: Size(250, 100),
                shape: RoundedRectangleBorder(
                  borderRadius: BorderRadius.circular(10),
                ),
              ),
              onPressed: () => {Navigator.of(context).pop()},
            )
            //削除ここまで
          ],
        ),
      ),
    );
  }
}

```

AppBar に戻るボタンが表示されるようになったので画面がすっきりしました。

ここまでやってさあスマホでテストしてみるぞ！　って思ったらなんか構成が足りないみたいです。
経験不足……。
