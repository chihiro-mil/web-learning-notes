# JavaScript出力方法
JavaScriptで結果を表示する方法が大きく分けて3種類ある

## １　コンソール(consoleオブジェクト)
```javascript
console.log('Hello');
```
開発者ツールのconsoleに表示される
主にプログラム動作テストで用いる

### console.log()
()内のテキストや数値を表示

### console.dir()
()内の複雑なデータをリスト表示

### console.error()
エラーをリスト表示

---

## ２　ダイアログボックス(windowオブジェクト)
```javascript
window.alert('Hello');
```
アラートダイアログボックスが表示される
ブラウザによって、ＯＫや閉じるボタンでボックスが閉じる


---

## ３　HTMLの書き換え(documentオブジェクト)
HTML
```html
<h1 id='title'>こんにちは</h1>
```
JavaScript
```javascript
document.getElementById('title').textContent = "変更";
```

処理の流れ
1. document →　HTML全体
2. getElementById（メゾット） →　指定idの要素を丸ごと取得（getElementByIdの場合）
※メゾットによって取得方法が変わる
3. textContent（textContentはプロパティ。プロパティはオブジェクトの状態を表す）　→ テキスト変更

結果

こんにちは →　変更

※JavaScriptは大文字・小文字を区別するのでgetElementByIdなどは書き方を間違えないように注意
