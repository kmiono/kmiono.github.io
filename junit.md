# JUnit入門

## JUnitとは

JUnit は、Java で作成したコードの単体テストを実施するツール  

## 実行環境

eclipse

### テスト対象とするコードの用意

*Higher.java*

```
public class Higher {
    public static void main(String[] args) {
        int a = 25;
        int b = -25;
        int higherNum = higher(a, b);
        System.out.printf(
               "より大きい数字は %d です. %n",
               higherNum
            );
    }
    public static int higher(int x, int y) {
        if (x > y) return x;
        return y;
    }
}
```

### テストメソッドの作成

次にテストメソッドを、Higher.java に追記します。 （実際は別でHigherTest.javaファイルを作りますが、入門なので） 

```
import static org.junit.Assert.assertEquals;
import org.junit.Test;
public class Higher {
    public static void main(String[] args) {
        int a = 25;
        int b = -25;
        int higherNum = higher(a, b);
        System.out.printf(
               "より大きい数字は %d です. %n",
               higherNum
            );
    }
    public static int higher(int x, int y) {
        if (x > y) return x;
        return y;
    }
    @Test
    public void testHigher() {
        assertEquals(25, higher(23, 25));
        assertEquals(5, higher(3, 5));
    }
}
```

## assertメソッドの種類

### assertEquals()

上記で使用。  
→　期待される結果と実際の結果が同じかどうか判定する。double、float以外の基本データ型およびオブジェクトの場合は、このメソッドを使用。
[TechscoreのJUnitのページのテストメソッド](https://www.techscore.com/tech/Java/Others/JUnit/2-2/)も参照すると「こういう使い方があるんだ」となれます。  
ちょっと分かりにくいので、「assertEquals （判定したい型）」で具体的な使い方を検索すると良いかもしれません。  

特にdouble型は注意みたいです。  
[テストとかでassertEqualsにdoubleを指定するときは注意](https://qiita.com/tao829/items/313ab27ca7ab94a11cf7)



### 参考

- [JavaBootCamp#10. JUnit テスト](https://fs5013-furi-sutao.github.io/java-bootcamp/advanced/10-junit-test)
- [JUnit入門（勉強メモ）](https://qiita.com/yuk0ga/items/74a0dbe36da02b358451)
- [TechscoreのJUnitのページ](https://www.techscore.com/tech/Java/Others/JUnit/index/)