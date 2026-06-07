# AboutFlutter
## ディレクトリ構成

### libディレクトリ
  実際のアプリのコードを記述していくディレクトリ。  
  「main.dart」というファイルがFlutterアプリのエントリーポイントとなる。

### Platformごとのディレクトリ
  ios, android, macなど、Platformごとのディレクトリ  
  libディレクトリに記述されたコードを各種Platformに対応したコードに変換する際に参照される。
  
### パッケージ管理ファイル
- pubspec.yaml
  パッケージの依存関係を記述する。
- pubspec.lock
  その依存関係を解決した結果を記述する。

### testディレクトリ
　Flutterのテストコードを記述するディレクトリ

### 


## Widget

画面を構成する塊。ボタン・テキスト・画像・レイアウトまですべてWidgetで構成される。

### StatelessWidget
状態を持たないWidget。状態変化に伴う画面の再描画が不要な場合に使う。  
例：ヘッダー、ホームタブ、固定テキスト

### StatefulWidget
状態を持つWidget。状態が変化した際にWidgetの再構築が必要となり、画面が再描画される。  
例：チェックボックス、入力フォーム、カウンター

### setState()
`StatefulWidget` 内で状態を変更する際に使う。  
`setState()` で囲むことで「状態が変わったので画面を再描画してください」とFlutterに伝える。

```dart
void _increment() {
  setState(() {
    _counter++; // setState()なしだと変数は変わるが画面は更新されない
  });
}
```

### runApp()
`main()` から呼び出され、引数のWidgetをアプリの画面として表示する。

```dart
void main() {
  runApp(const MyApp()); // MyAppをアプリのルートWidgetとして表示
}
```

## 状態（State)について
状態を管理するクラス：Stateクラス  
自身が持つ変数の更新を検知すると、buildメソッドを再度呼び出す。  
→ 変数が変わるたびに、Widgetツリーを再描画する。  (丸ごと破棄され、またイチから再生成されるイメージ）

## API呼び出し
### httpパッケージ
FlutterからAPI通信を行う際は、httpやdioといったパッケージを活用する。


