# AboutClassOfDart (Dartのクラスについて）
Dartにおける言語仕様の中でも「クラス」をピックアップしています。

## Enum（列挙型）
固定された数の定数を管理する特殊なクラス

### Enumの宣言
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
