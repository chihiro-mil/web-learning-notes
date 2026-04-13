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