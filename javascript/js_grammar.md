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

上記**変数**の処理の流れ
1. promptダイアログを表示
2. ユーザーが文字を入力
3. 入力された文字が返される
4. 入力された文字（例：はい）が変数answerに代入される
5. console.logで「はい」が表示


```javascript
const answer = window.prompt('開始しますか？');
console.log(answer);
```

上記**定数**の処理の流れ
1. promptダイアログを表示
2. ユーザーが文字を入力
3. 入力された文字が返される
4. 入力された文字（例：はい）が定数answerに代入される
5. console.logで「はい」が表示
6. 定数answerは代入された値を後から変更することはできない


## 条件分岐（else if）
２つ以上の条件式を使って、上から順に評価結果が条件に当てはまるかどうかをチェックしていく

```javascript
const answer = window.prompt('開始しますか？');
if(answer === 'yes') {
    window.alert('ゲームを開始します');
} else if(answer === 'no') {
    window.alert('ゲームを中止します');
} else {
    window.alert('yesかnoでお答えください');
}
console.log(answer);
```

処理の流れ
1. promptダイアログを表示
2. ユーザーが「yes」を入力した時 → 「ゲームを開始します」が表示
3. ユーザーが「no」を入力した時 → 「ゲームを中止します」が表示
4. ユーザーが「yes」か「no」を以外を入力した時 → 「yesかnoでお答えください」が表示
※answer === 'yes'は入力が完全一致でないと「yesかnoでお答えください」が表示される。
(answer.toLowerCase() === 'yes')で小文字や大文字でも「ゲームを開始します」が表示


## JavaScriptの演算子
- a === b   aとbが同じ時True
- a !== b   aとbが同じではない時True
- a < b     aがbより小さい時True
- a <= b    aがb以下の時True
- a > b     aがbより大きい時True
- a >= b    aがb以上の時True


## 複数の条件式を組み合わせて１つの条件を作る
- &&演算子

```javascript
if(number >= 10 && number < 25);
```

例）numberが10以上　かつ　25より小さい時Trueになる
両方の条件を満たす時に実行される

- ||演算子

```javascript
if(number === 10 || number === 25);
```

例）numberが10　もしくは　25時Trueになる
片方どちらか、もしくは両方の条件を満たす時に実行される


## While文
繰り返し同じような処理を何度も実行したい時に使う

```javascript
let number = 1;
while(number <= 10) {
    console.log(number);
    number = number + 1;
}
```

処理の流れ
1. 変数numberに数字の1を入れる
2. While文の条件（number <= 10）がTrueの間、処理を繰り返す
3. 繰り返しの中でnumberに1を足す
　例）１回目　number(1) + 1 = 2、　２回目　number(2) + 1 = 3、 ・・・結果が10になるまで

**無限ループに注意**
常にTrueになってしまう条件式を書いてしまうと、処理が止まらなくなってしまう。

## ファンクション（関数）
何度も行う処理を１つにまとめる小さいサブプログラム

```javascript
function total(price) {
    const tax = 0.1;
    return price + price * tax;
}

console.log('服の値段は' + total(5000) + '円（税込）です。');
document.getElementById('price').textContent = '服の値段は' + total(5000) + '円（税込）です。';
```


処理の流れ
1. ファンクション名から要求されたパラメータを受け取る（本体価格5000を受け取る）
2. 5000×0.1　→　本体価格＋税金価格　の計算処理を実行
3. 計算結果(戻り値)を呼び出し元に返す　　服の値段は5500円（税込）です。

```javascript
function total(price) {
    const tax = 0.1;
    return price + price * tax;
}

document.getElementById('price').textContent = '服の値段は' + total(5000) + '円（税込）です。';
document.getElementById('price2').textContent = 'アウターの値段は' + total(10000) + '円（税込）です。';
document.getElementById('price3').textContent = '靴の値段は' + total(8000) + '円（税込）です。';

```

**利点**
- ファンクションを使うことでtotal(price)の処理を何度も呼び出しできる
- 税金を変更したい時に一か所変えるだけ（const tax = 0.1;を変更するだけ）ですべての税金が変更できる


## 配列
複数のデータを１つにまとめて、順番に管理できる仕組み
let 変数名　= [データ0, データ1, データ2];

```javascript
let list = ['航空券', '洋服', '化粧品', 'デジカメ'];
for(let item of list) {
    console.log(item);
}
```

処理の流れ
1. let 変数名　= [データ0, データ1, データ2]; で配列を作成
2. for文で変数（list）の中にある１つずつ取り出し、変数（item）に代入
3. 取り出したitemをconsole.logで順番に表示


**注意**
配列データを指定して取り出す場合はインデックス（0から始まる）の番号に注意


**配列にデータを追加・削除するメゾット**
- 配列最後のデータを削除　→　変数（配列）.pop()
- 配列最後にデータを追加　→　変数（配列）.push(データ)
- 配列最初のデータを削除　→　変数（配列）.shift()
- 配列最初にデータを追加　→　変数（配列）.unshift(データ)


## オブジェクト
様々なデータをまとめて、１つの変数として扱う
オブジェクトの作成方法
let 変数名　= {プロパティ名１: データ, プロパティ名２: データ, プロパティ名３: データ};

オブジェクトからデータを読み取る方法は２つ
- オブジェクト名.プロパティ名
- オブジェクト名['プロパティ名'] ←シングルクォート（ダブルクォート可）を忘れずにつける

プロパティのデータを書き換える方法は２つ
- オブジェクト名.プロパティ名 = 新しいデータ;
- オブジェクト名['プロパティ名'] = 新しいデータ;

```javascript
let book = {title: 'python', price: 3000, stock: 5};
console.log(book);

book.stock = 15;
console.log(book.stock);
```

処理の流れ
1. let book　= {プロパティ名１: データ, プロパティ名２: データ, プロパティ名３: データ}; でオブジェクトを作成
2. console.log(book);　でオブジェクトの全体のデータが表示
3. book.stock = 15;　でstockのデータを書き換え
4. console.log(book.stock);　でstockのデータのみ表示


for文をつかってすべてのプロパティを読み取る場合

```javascript
let book = {title: 'python', price: '3000', stock: 5};
for(let p in book) {
    console.log(p + '=' + book[p]);
}
```

処理の流れ
1. let book　= {プロパティ名１: データ, プロパティ名２: データ, プロパティ名３: データ}; でオブジェクトを作成
2. for(let p in book)　で{}の中の処理内容をプロパティ（p）のキー分繰り返す
3. console.log(p + '=' + book[p]);　で pでプロパティ、book[p]でデータを取得　→　「title=python」のように表示


**注意**
for文は配列ように順番に表示されるとは限らない。（上記の例　title、price、stockは記載順には表示されない場合がある）