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
