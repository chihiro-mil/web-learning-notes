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

