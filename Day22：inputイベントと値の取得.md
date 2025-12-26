
## 1.基本の書き方



**Step1：HTMLに入力欄を用意する**

<input id="textInput" />

意味
input：文字を入力する部品

id="textInput"：JSからこの入力欄を特定する名前



**Step2：JavaScriptで入力欄を取得する**

const input = document.getElementById("textInput");


何をしているか（超短く）

document：画面全体

getElementById：idで探す

"textInput"：さっき付けた名前

input：JS側で使う箱

👉 これで
「JSが入力欄そのものをつかんだ」 状態です。



**Step3：inputイベントをつける**

input.addEventListener("input", function () {
  console.log("入力された");
});

何が起きるか（1行）

文字が1文字でも変わるたびに、この中が実行されます。

ここで大事な事実

今このコードは👇

何が入力されたか 見ていない
ただ「入力された瞬間」を 検知しているだけ

つまりこれは
「合図」だけ を受け取っている状態です。



**Step4：入力された「値」を取得する**

input.addEventListener("input", function () {
  console.log(input.value);
});


何が変わったか

input：入力欄そのもの

input.value：今入力されている文字

👉 これで
画面 → JS に文字が渡った 状態になります。


**超重要（ここだけ覚えてください）**

input        // 入力欄（物）
input.value  // 入力された文字（データ）

value を見に行かない限り、文字は取れません。

動作イメージ↓

文字を打つ

inputイベント発生

JSが value を読む

consoleに表示される



addEventListener
→ 出来事を待ち受ける仕組みを追加する

"input"
→ 文字が入力・削除された瞬間

function () { ... }
→ 起きたら実行する処理

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

## 2.練習問題

入力された文字を console に表示するコードを書いてください。

条件

id="nameInput" の input を使う
input イベントを使う
入力された文字を console.log する

ヒント（最小）

document.getElementById
addEventListener
.value

👉 コードを書いて貼ってください。



<input id="nameInput"/>

const input = document.getElementById("nameInput");

input.addEventListener("input" , function () {
  console.log(input.value);
});



とても良いです。ほぼ満点です。

⚠️ 1点だけ注意（超重要）
<input id="nameInput"/>

この HTMLとJSは別ファイル で書くのが前提です。


**修正版**

<input id="nameInput"/>
<script src="script.js"></script>

const input = document.getElementById("nameInput");

input.addEventListener("input" , function () {
  console.log(input.value);
});

いい修正です 👍
構造として正しくなりました。

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

## 3.練習問題

入力された文字を一度変数に入れてから表示してください。

条件

変数名は text
input.value を直接 console.log しない

<input id="nameInput"/>
<script src="script.js"></script>

const text = document.getElementById("nameInput");

text.addEventListener("text" , function () {
  console.log(text);
});


① 間違い①：イベント名 "text"
② 間違い②：console.log(text)

③ 練習問題②の条件を思い出してください

変数名は text

input.value を直接 console.log しない

つまり必要なのは👇
「別の変数」に value を入れること です。


**修正版**

<input id="nameInput"/>
<script src="script.js"></script>

const input = document.getElementById("nameInput");

input.addEventListener("input" , function () {
  const text = input.value;
  console.log(text);
});



いいです。その理解の修正が今日いちばん大事なポイントです。
結論から言います。

✅ 今のコードは【完全正解】です

input
→ 画面の部品（HTML要素）

input.value
→ ユーザーが入れたデータ

text
→ JSで扱うために保存したデータ

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

## 4.練習問題（最後・軽い応用）

入力された文字を
「入力された内容：〇〇」
という形で console に表示してください。

条件

文字連結 or テンプレート文字列どちらでもOK

text 変数は使う



<input id="nameInput"/>
<script src="script.js"></script>

const input = document.getElementById("nameInput");

input.addEventListener("input" , function () {
  const text = input.value;
  console.log("入力された内容：" + text);
});

完璧です 👍
練習問題③も正解。Day22は完全終了です。

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

🟦 Day22：inputイベントと値の取得（JS基礎）

今日は、
ユーザーの入力を「データとしてJavaScriptに渡す仕組み」
を理解し、実際にコードで確認した日です。



■ 今日、まず理解したこと（超シンプルに）

入力欄（input）はデータではない。
データが入ってくる「入口」である。

ユーザーが文字を打っても、
JavaScriptが自分から取りに行かない限り、
その文字は「存在しない」のと同じ。



■ 今日の本質的な理解ポイント

✔ 1) HTMLの要素 と JavaScriptのデータは別物

HTMLの input
→ 画面上の部品（要素）

input.value
→ その部品の中に入ったデータ（文字）

この2つを混同すると、
「何を扱っているのか分からなくなる」状態になる。


✔ 2) inputイベントの役割

addEventListener("input", ...)

これは
「入力が変わったら教えてほしい」
とブラウザにお願いする仕組み。

click → 押したとき

input → 入力が変わったとき

イベント＝合図
であり、処理そのものではない。


✔ 3) データはJS側の変数に入れて扱う

const text = input.value;

ここで初めて、

画面の中の文字
→ JavaScriptが扱えるデータ

に変換される。

要素（input）と、
その中身（text）を分けて考える
という感覚を身につけた。



■ 今日コードを書いて理解した流れ

HTMLのinput要素をJSで取得する

inputイベントで入力の変化を検知する

value を使って入力文字を取り出す

JSの変数として扱う

この流れが
画面 → JavaScript → データ
の基本構造だと理解した。



■ 今日の気づき・修正できた誤解

「変数名を変えれば意味も変わる」と思っていたが違った

要素を入れる変数と、データを入れる変数は役割が違う

console.log(input) と console.log(input.value) の違いが明確になった



■ Day22の最終的な理解（1文）

inputイベントで入力の変化を検知し、
value を使って入力内容をJavaScriptのデータとして扱う。