# AboutDart

## 特徴
### 1. 静的型付け言語である
```Dart
final int number  = 10;   // 数値型
final String kazu = '10'; // 文字列型

void myFunction(int data){
  print(data);
}

void main(){
  myFunction(number);  // OK(10)
  myFunction(kazu);    // NG

> Error : The argument type 'Type' can't be assigned to the parameter type 'int'.
}

```

#### 動的型付けも可能

```Dart
final int number  = 10;   // 数値型
final String kazu = '10'; // 文字列型

void myFunction(dynamic data){
  print(data);
}

void main(){
  myFunction(number);  // OK(10)
  myFunction(kazu);    // OK(10)

}

```




### 2. オブジェクト指向言語（OOP）である
###  オブジェクト指向

```dart
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
--- 


#### クラス
役割: 設計書  
- どのような値（変数）を保持し、どのような動き（関数）をするのかあらかじめ定義したもの。

--- 

#### コンストラクタ
役割：初期化
- クラスからインスタンスを生成するために必要な関数
- インスタンス生成時に、コンストラクタを通じて実行メモリを確保する。
---

#### インスタンス
役割：具体的なデータ
- コンストラクタによってメモリ上に生成された具体的なデータ
---


## 変数

| 変数宣言 | システム制約 | 使用用途 |
|:-----------|------------:|:------------:|
| String name      | 必須入力 (null不可)        |  必ず入力が必要なもの（名前など）      |
| String? name     | 任意入力（null可）      | 任意入力のプロフィール項目       |
| final String id       | 実行時、値確定       |   ユーザID       |
| const String pi         | コンパイル時、値確定         |    Appのテーマ色や余白など。不変なもの        |


## データ型
| type | content | examle |
|:-----------|------------:|:------------:|
List | 配列 | List<String>[] |
Set | （重複のない）数列 | Set<int>{} |
Map | 連想配列 | Map<String, int>{} |

### List
順序を持つ複数の要素を保持する配列のこと。※ 重複不可

```Dart
//定義
List<String> fruits = [apple, orange, grape];
List<int> numbers   = [1, 3, 5, 7, 9];


void main() {
//要素の取得 (index)
  print(fruits[0]);  // > 'apple'
  print(numbers[1]); // > 3

//要素の追加・更新
  fruits.add('banana');     // [apple, orange, grape, banana]
  numbers[0] = 10;          // [10, 3, 5, 7, 9]

//要素の削除
  fruits.remove(banana);
  numbers.remove(numbers[0]);

//要素の確認
  fruits.contains('apple'); //true
  numbers.contains(1);      //false

//要素数の確認
  fruits.length // 5

//その他操作
  List<int> moreNumbers = [2, 4, 6];
  numbers.addAll(moreNumbers); //[10, 3, 5, 7, 9, 2, 4, 6]
}
```

### Set
重複を許さない要素を保持する配列のこと。  
Setは要素の順序をせず、重複する要素は一つにまとめられる。  
→ Setは、ユニークな要素の集合を管理する際に便利です。

```Dart
//定義
Set<String> country = {'Japana', 'Korean', 'China'};
```


### Map
キーと値をペアにして要素を保持する配列のこと。  
キーと値は１対１の関係であり、キーを利用して値を取得できる。  
※キーが重複したMapを定義してもエラーは発生せず、1つ目が表示されるのみ。

```Dart
//定義
Map<int, String> errorMsgList = {
  403 : 'Forbidden',
  404 : 'Not Found',
  500 : 'Internal Server Error',
  502 : 'Bad GateWay',
}

void main()
  //要素の取得
  String? errorMsg = errorMsgList[403];  //'Forbidden'

  //要素の追加・更新
  errorMsgList[504] = 'Unknown Error';   //追加
  errorMsgList[504] = 'GateWay Unknown'; //既存のキーに一致する値を更新

  //要素の確認
  //キーをもとに検索
  bool hasGateWayUnknown = errorMsgList.containsKey(504);     //true
  bool hasNotFound = errorMsgList.containsValue('Not Found'); //true

  //要素の削除
  errorMsgList.remove(504);

  //すべてのキーと値を取得
  Iterable<int> errorCode    = errorMsgList.keys;
  Iterable<String> errorMsg  = errorMsgList.values;
}
```

## 関数
- 返り値の型 関数名（引数の型 引数名) {処理 return 返り値;}
- void 関数名 (引数の型 引数名) {処理 return;}

```Dart
//定義 (返り値あり）
String numToStr(int number){
  return number.toString();
}

//定義 (返り値なし）
void doGreet() {
  print('Hello');
  return;
}

//呼び出し
void main(){
  doGreet();
  final number = numToString(15);
}

```
