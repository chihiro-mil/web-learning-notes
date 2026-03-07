# JavaScriptの文法

## 条件分岐（if）
ある条件が成り立つかどうかで動作を変える

条件によって動作が変わるものはほぼすべて**ブール（ブーリアン）値**（True/False）で評価して次に実行する処理を決める

if(条件式) {
    条件式がTrueの時に実行される処理
} else {
    条件式がFalseの時に実行される処理
}

```javascript
if(window.confirm('開始しますか？'))　{
    console.log('開始します'); 
} else {
    console.log('終了します');
}
```

処理の流れ
1. windowオブジェクトのconfirmメゾットを使い確認ダイアログボックス表示
2. 「開始しますか？」の返答に「OK」をクリックした時　→　戻り値がTrueになり、「開始します」が表示
2. 「開始しますか？」の返答に「キャンセル」をクリックした時　→　戻り値がFalseになり、「終了します」が表示


---

## 変数・定数　入力内容によって動作を変更
変数：データを保存して後の処理でも使えるようにするもの
**let　〇〇**で入力

```javascript
let answer = '開始しますか？';
```

定数：代入したデータを書き換えることができない
**const　〇〇**で入力

```javascript
const title = '開始しますか？';
```

```javascript
let answer = window.prompt('開始しますか？');
console.log(answer);
```

処理の流れ
1. promptダイアログを表示
2. ユーザーが文字を入力
3. 入力された文字が返される
4. 入力された文字（例：はい）が変数answerに代入される
5. console.logで「はい」が表示
