# AboutDart

## オブジェクト指向
```

void main() {
  //インスタンス生成
  var person = Person(age:25, name:'匿名', address='大阪府');

  person.introduce();    //「私は匿名です。」
  print(person.address); //「大阪府」

}



// クラス
class Person {
  //インスタンス変数
  int? age;                //null許容型
  final String name;
  String address

  //名前付きコンストラクタ
  Person({this.int, required this.name, this.address = '東京都'});

  void introduce() {
    print('私は$nameです');
  }
}
```



### クラス
役割: 設計書  
- どのような値（変数）を保持し、どのような動き（関数）をするのかあらかじめ定義したもの。

### コンストラクタ
役割：初期化
- クラスからインスタンスを生成するために必要な関数
- インスタンス生成時に、コンストラクタを通じて実行メモリを確保する。

### インスタンス
役割：具体的なデータ
- コンストラクタによってメモリ上に生成された具体的なデータ

---

## 文字列補間

```dart
String name = 'Flutter';
print('Hello, $name!'); // → Hello, Flutter!
```

- `$変数名` を使うと文字列に変数の値を埋め込める
- `+` 演算子で連結するより読みやすい

---

## 関数

```dart
// 戻り値の型 関数名(引数の型 引数名)
String greet(String name) {
  return 'Hello, $name!';
}

// 戻り値なし
void printHello() {
  print('Hello!');
}
```

- 戻り値の型を関数名の前に書く
- 戻り値がない場合は `void`

---

## for文

```dart
int count = 3;
for (int i = 0; i < count; i++) {
  print(i); // 0, 1, 2 の順に出力（3回）
}
```

- `i < count` の条件が `false` になった時点でループ終了
- `i = 0` から始まり `i = 2` まで実行される（ちょうど3回）
