# Firebase Auth - サインアップ実装

## createUserWithEmailAndPassword

Firebase でメール/パスワードのアカウントを作成するメソッド。名前付き引数で渡す。

```dart
await FirebaseAuth.instance.createUserWithEmailAndPassword(
  email: email,
  password: password,
);
```

## onPressed には関数を渡す

関数を実行した結果ではなく、関数そのものを渡す。

```dart
// NG: 画面表示時に即実行される
onPressed: someFunction()

// OK: ボタンを押したときに実行される
onPressed: () async {
  await someFunction();
}
```

## async / await

- `await` をつけた処理が完了するまで、次の行の実行を待つ
- `async` と `await` はセット。`async` なしに `await` は使えない

```dart
Future<void> createUser() async {
  await FirebaseAuth.instance.createUserWithEmailAndPassword(...); // 完了を待つ
  // ↑ 完了後に次の処理へ進む
}
```

## FirebaseAuthException でエラーを判別

```dart
try {
  await FirebaseAuth.instance.createUserWithEmailAndPassword(...);
} catch (e) {
  if (e is FirebaseAuthException) {
    if (e.code == 'email-already-in-use') {
      print('既にそのメールアドレスは利用されています。');
    } else if (e.code == 'weak-password') {
      print('パスワードが脆弱です。');
    } else if (e.code == 'invalid-email') {
      print('不正なメールアドレスです。');
    }
  }
}
```

| code | 意味 |
|------|------|
| `email-already-in-use` | メールアドレスが登録済み |
| `weak-password` | パスワードが短すぎる |
| `invalid-email` | メールアドレスの形式が不正 |

## dispose() はメモリリーク防止

`TextEditingController` は画面が閉じてもメモリに残り続ける。`dispose()` で明示的に解放する。

```dart
@override
void dispose() {
  _mailController.dispose();
  _pwController.dispose();
  super.dispose();
}
```
