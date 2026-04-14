# AboutClassOfDart (Dartのクラスについて）
Dartにおける言語仕様の中でも「クラス」をピックアップしています。

## Enum（列挙型）
固定された数の定数を管理する特殊なクラス

### 1.Enumの宣言
```
enum Color {
  Red,   // index = 0
  Blue,  
  Yellow,
  White,
  Black  // index = 4
}

void main() {
  var themeColor = Color.Red

  // Enumの利用
  print(themeColor.index)  // 0
  print(themeColor.name)   // Red (文字列型）
}

```

### 2.任意プロパティを持つEnumの宣言
```
enum ConnectionState {
  // 定数定義と引数渡し
  connected(200, '接続成功'),
  timeout(404, 'タイムアウト'),
  error(500, 'サーバーエラー'); // ここはセミコロン ; が必須

  // フィールド定義
  final int code;
  final String label;

  // コンストラクタ（const必須）
  const ConnectionState(this.code, this.label);

  // メソッドやGetterも定義可能
  bool get isError => code >= 400;
}

void main() {
  var state = ConnectionState.timeout;

  print(state.code);  // 408
  print(state.label); // タイムアウト
  print(state.isError); // true
}

```
