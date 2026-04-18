# イベント
イベントを使用することによって、プログラムが動作するタイミングを制御することができる。

## 要素にイベントを設定する時

取得した要素.イベント = function {
    処理内容
};

```javascript
document.getElementById('form').onsubmit = function() {
    alert('フォームが送信されました');
};
```

処理の流れ
1. htmlのformの要素を取得
2. submitイベントを設定
3. フォーム送信時（submitイベント発生時）に処理が実行（アラート表示）


## イベントを使って画面遷移の制御やフォーム内容を読み取る


```html
<form action="#" id="form">
        <input type="text" name="word">
        <input type="submit" value="検索">
    </form>

    <p id="output"></p>
```

```javascript
document.getElementById('form').onsubmit = function(event) {
    event.preventDefault();
    const search = document.getElementById('form').word.value;

    if (search === '') {
        document.getElementById('output').textContent = 'キーワードを入力してしてください';
        return;
    }
    document.getElementById('output').textContent = search + 'を検索しています．．．';
};
```

上記例題から
- 画面遷移の制御　→　function(event) {event.preventDefault()　　・・・　};
event.preventDefault()でフォーム送信によるページ遷移をキャンセル

- 入力内容を読み取る　→　const search = document.getElementById('form').word.value;
処理の流れ
1. document.getElementById('form')でHTMLの<form>～</form>の要素を取得
2. <input type="text" name="word">で読み取りたい部分をname属性で指定
3. .wordでinput要素を取得
4. .valueで入力された文字列を取得


# Dateオブジェクト
## 現在の日時を分かりやすく表示する
Dateオブジェクトをそのまま使用すると見慣れない表示になってしまうため、分かりやすく加工する

```html
<p>現在の日時：<span id="time"></span></p>
```

```javascript
const now = new Date();
const year = now.getFullYear();
const month = now.getMonth();
const date = now.getDate();
const hour = now.getHours();
const min = now.getMinutes();

const output = `${year}/${month + 1}/${date} ${hour}:${min}`;
document.getElementById('time').textContent = output;
```

処理の流れ
1. new Date()　基準となる日時の情報が必要のため現在の日時を取得（未来や過去から計算する時なども現在日時の取得は基本）
2. 基準となる日時の情報を記憶した状態で年/月など個別に必要な情報を取得
3. output定数に分かりやすい表示に整えた内容を代入
4. <span id="time"></span>のtextContentプロパティに代入

**注意**
1. getMonthは仕様として0～11を返す（1月が0）ため、人間が理解しやすい月にするには+1が必要
ほかにズレが生じてしまう代表的なメゾットのgetDay（曜日が0(日)）もある
2. new Date()のように、Dateオブジェクトはnewを使ってインスタンス化（初期化）する必要がある