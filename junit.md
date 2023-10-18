# JUnit 入門

## JUnit とは

JUnit は、Java で作成したコードの単体テストを実施するツール

## 実行環境

eclipse

プロジェクトはeclipse上で右クリック→新規Javaプロジェクトを選択しましょう。  
テストファイルの作成に関しては下記記事を参考にすると分かりやすいかと思います。  
[Java JUnit4 の使い方とテストのサンプル](https://itsakura.com/java-junit)  


### テスト対象とするコードの用意

```
class Color1 {
	String getColor(int i) {

		if (i == 1) {
			return "赤";

		} else if (i == 2) {
			return "青";

		} else {
			return "1or2を入力して下さい";
		}
	}
}
```

### テストコードの作成

次にテストコード作成します。

```
import static org.junit.Assert.*;
import org.junit.Test;
import static org.hamcrest.CoreMatchers.*;

public class Color1Test {

	@Test
	public void testGetColor1() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(1);
		assertThat(t1,is("赤"));
	}
	@Test
	public void testGetColor2() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(2);
		assertThat(t1,is("青"));
	}
	@Test
	public void testGetColor3() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(3);
		assertThat(t1,is("1or2を入力して下さい"));
	}
}
```

## assert メソッドの種類

### assertThat

上記で使用した assert メソッド。

JUnit5 以前のテストでは、assertThat に Matcher API を組み合わせます。上記は assertThat + is のテストになります。こちらは値を比較し、期待値が出力されているかをテストしたものです。  
また別の assert メソッドで assertEquals という似たものもあります。こちらは JUnit5(JUnit Jupiter)で使われているようです。  
assertThat は JUnit4 で使用するのですが、最新版でないためかテストファイルに記述してみると打消し線が引かれてしまうことがあります（動きます）

assertEquals その他について：  
[JUnit 入門（勉強メモ）](https://qiita.com/yuk0ga/items/74a0dbe36da02b358451)  
ざっくり「これはこんな役割」という概略が書かれています。

### Matcher API

#### is

値を比較する際に使用（上記のテストケースがその一例です）

```
@Test
public void isを試す() {
	assertThat("Hello", is("Hello"));
	assertThat(1, is(1));
}
```

#### not

比較した結果が false であることを確かめるテストです

```
@Test
public void notを試す() {
	assertThat("Hello", is(not("bye")));
}
```

##### テストプログラム

```
class Color2 {
	String getColor(int i) {

		if (i == 1) {
			return "赤";

		} else if (i == 2) {
			return "青";

		} else {
			return "1or2を入力して下さい";
		}
	}
}
```

```
import static org.junit.Assert.*;
import org.junit.Test;
import static org.hamcrest.CoreMatchers.*;

public class Color2Test {

	@Test
	public void testGetColor1() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(1);
		assertThat(t1,is("赤"));
	}
	@Test
	public void testGetColor2() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(2);
		assertThat(t1,is(not("オレンジ")));
	}
	@Test
	public void testGetColor3() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(3);
		assertThat(t1,is("1or2を入力して下さい"));
	}
}

```

→ 　 testGetColor2 のみが成功するかと思います（i = オレンジではない）

#### null value

null であることを確かめます

##### テストプログラム

```
class Color3 {
	String getColor(int i) {

		if (i == 1) {
			return "赤";

		} else if (i == 2) {
			return "青";

		} else {
			return null;
		}
	}
}
```

```
import static org.junit.Assert.*;
import org.junit.Test;
import static org.hamcrest.CoreMatchers.*;

public class Color3Test {

	@Test
	public void testGetColor1() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(1);
		assertThat(t1,is("赤"));
	}
	@Test
	public void testGetColor2() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(2);
		assertThat(t1,is("青"));
	}
	@Test
	public void testGetColor3() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(3);
		assertThat(null, nullValue());
	}
}

```

#### notNullValue

null でないことを確かめます

```
class Color4 {
	String getColor(int i) {

		if (i == 1) {
			return "赤";

		} else if (i == 2) {
			return "青";

		} else {
			return "1or2を入力して下さい";
		}
	}
}
```

```
import static org.junit.Assert.*;
import org.junit.Test;
import static org.hamcrest.CoreMatchers.*;

public class Color4Test {

	@Test
	public void testGetColor1() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(1);
		assertThat(t1,is("赤"));
	}
	@Test
	public void testGetColor2() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(2);
		assertThat(t1,is(not("オレンジ")));
	}
	@Test
	public void testGetColor3() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(3);
		assertThat("1or2を入力して下さい",is(notBullValue()));
	}
}

```

#### instanceOf(isA)

指定した型と同一であるかを確かめます。

```
class Color5 {
	String getColor(int i) {

		if (i == 1) {
			return "赤";

		} else if (i == 2) {
			return "青";

		} else {
			return "1or2を入力して下さい";
		}
	}
}
```

```
import static org.junit.Assert.*;
import org.junit.Test;
import static org.hamcrest.CoreMatchers.*;

public class Color5Test {

	@Test
	public void testGetColor1() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(1);
		assertThat("赤",instanceOf(String.class));
	}
	@Test
	public void testGetColor2() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(2);
		assertThat("青",instanceOf(String.class));
	}
	@Test
	public void testGetColor3() {
		Color1 c1 = new Color1();
		String t1 = c1.getColor(3);
		assertThat("1or2を入力して下さい",instanceOf(String.class));
	}
}

```

基礎的なものを列挙しました。

さらに多くの Matcher を知りたいという方はこちら ↓  
[Hamcrest の Matchers に定義されているメソッドの使い方メモ](https://qiita.com/opengl-8080/items/e57dab6e1fa5940850a3)を一読してみると良いかもしれません。

公式（？）のドキュメントとしては[Hamcrest Javadoc](https://hamcrest.org/JavaHamcrest/javadoc/1.3/org/hamcrest/CoreMatchers.html)がありますが、英語＋文章が分かりづらいので、どなたかが噛み砕いてくださった記事をまず参考にするのが良いのかなと。

### 読んだけどどれで何するのか忘れた！

落ち着いてください。まずは Google 先生に「JUnit 　(テストしたいこと)」を尋ねましょう。

### 参考

- [JUnit 入門（勉強メモ）](https://qiita.com/yuk0ga/items/74a0dbe36da02b358451)
- [JUnit の使い方（初級）](https://qiita.com/YutaSaito1991/items/46707049d0a26086b443)
- [Java JUnit4 の使い方とテストのサンプル](https://itsakura.com/java-junit)
- [Hamcrest の Matchers に定義されているメソッドの使い方メモ](https://qiita.com/opengl-8080/items/e57dab6e1fa5940850a3)
- [Hamcrest Javadoc](https://hamcrest.org/JavaHamcrest/javadoc/1.3/org/hamcrest/CoreMatchers.html)
