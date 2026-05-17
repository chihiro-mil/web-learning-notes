# ケバブメニュー開閉手順
アイテム一覧のアイテム１つ１つにケバブメニューをつけて、ケバブメニュータップ後削除と編集ボタンを表示させたい

## JavaScriptの処理の流れ
1. ケバブボタン全部取得　　画面内にあるすべてのケバブボタンを取得（複数のケバブメニューがあるため。この処理がないとどのボタンを押したのかの情報が得られなくなる）
2. ケバブボタン１個ずつにクリックイベントを付ける　　取得したボタン１つ１つにクリック処理を設定する
3. 押されたボタンのカード取得　クリックされたボタンがどのカードの中にあるか探す（この処理がないとすべてのメニューまたは違うカードのメニューが開いてしまう可能性あり）
4. 押されたボタンのカードのメニュー取得　　メニューもカードごとに存在するため
5. メニューの表示・非表示を切り替える

## 必要なHTML構造
```html
<div class="item-card"> #上記処理の(３)に必要な目印　※今回は同じカードが複数あるためidではなく、classを使う
    <button class="kebab-btn"> #上記処理の(１)(２)に必要な目印
        : 
    </button>
    <div　class="kebab-menu"> #上記処理の(４)(５)に必要な目印
        <button class="edit-btn">
        編集
        </button>
        <button class="delete-btn">
        削除
        </button>
    </div>
</div>
```

## JavaScriptの処理の流れを参考にコードを書く

```javascript
const kebabButtons = document.querySelectorAll(".kebab-btn");  //上記(１)　定数「kebabButtons」定義して、条件に合うすべての要素を取得するメゾットquerySelectorAll()使用
kebabButtons.forEach(button => {
    button.addEventListener("click", () => {
        const card = button.closest(".item-card");
        const menu = card.querySelector(".kebab-menu");
        menu.classList.toggle("show");
    });
});
/*上記(２)　kebabButtons.forEach(button => ですべてのケバブボタンを1個ずつ取り出して(forEach)buttonという名前を使う。button.addEventListener("click" でクリックイベント追加
上記(３)　const card = button.closest　でクリックされたbuttonの一番近い親要素を探すため、closestメゾットを使用
上記(４)　const menu = card.querySelector (３)で取得したカードの中から.kebab-menuを探すため、querySelectorメゾットを使用
上記(５)　menu.classList.toggle("show");  (４)で取得したメニュー情報をclassList機能（プロパティ）を使って、toggleメゾットを実行
showクラスを付け外しすることでCSS（下記コード）でメニューの表示・非表示を切り替えられる
*/
```

```css
.kebab-menu {
    display: none;
}
.kebab-menu.show {
    display: block;
}
```