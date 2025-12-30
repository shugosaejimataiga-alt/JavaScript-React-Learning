
## 1.基本の書き方（DOM更新の最小セット）

今日は 2つだけ 覚えます。


**1️⃣ 文字を入れ替える（textContent）**

<p id="message">こんにちは</p>

const message = document.getElementById("message");
message.textContent = "こんばんは";


何が起きているか

HTMLの <p> はそのまま
中の文字だけが変わる
画面表示が即座に更新される

👉 「文章を書き換える」ための更新


**2️⃣ 要素を追加する（append）**

<ul id="list"></ul>

const list = document.getElementById("list");

const li = document.createElement("li");
li.textContent = "りんご";

list.append(li);


何が起きているか

追加先を取る
新しい要素を作る
appendで入れる

👉 「表示を増やす」ための更新



**ここで重要な整理**

textContent → 置き換え

append → 追加

DOM更新は
「消す / 変える / 増やす」 の3種類しかありません。
今日は 変える・増やす を扱っています。

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

## 2.練習問題（超シンプル・1問だけ）

問題
次の HTML があります。

<p id="count">0</p>


👉 JavaScriptで
この「0」を「1」に変えて表示してください。

条件：
textContent を使う
append は使わない
✋ コードを書いて送ってください。



<p id="count">0</p>

const count = document.getElementById("count");

count.textContent = "1";



正解です。
Day24の目的をきちんと達成できています。

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

## 3.練習問題

問題
次の HTML があります。

<ul id="fruits"></ul>


👉 JavaScriptで
「バナナ」という <li> を1つ追加してください。

条件：

createElement
textContent
append

を使う

✋ コードを書いて送ってください。



<ul id="fruits"></ul>


const list = document.getElementById("fruits");

const li = document.getElementById("li");
li.textContent = "バナナ";

list.append(li);



いいところまで来ています。
1点だけ修正すればOKです。

問題点（1つだけ）
👉 li は「取得」ではなく「新しく作る」必要があります。


**練習問題修正版**

<ul id="fruits"></ul>


const list = document.getElementById("fruits");

const li = document.createElement("li");
li.textContent = "バナナ";

list.append(li);


完璧です。
append の本質を正しく理解できています。

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

## 4.疑問：

これを本番はどう使うのですか？
人生to doアプリの際に



とても良い疑問です。「勉強 → 本番」のつながりを今ここで整理します。

結論（先に）

今日やった DOM更新は、本番ではこう使われます。

textContent → 進捗％・件数・タイトル表示
append → ToDo / Action / Dream の一覧表示

つまり
👉 「ユーザー操作でデータが変わり、それを画面に反映する」
その最小単位が今日の内容です。



人生ToDoアプリでの具体対応（JS時代）

**① 追加（append が活きる場面）**

例：Actionを追加する

入力欄に文字を書く
追加ボタンを押す
JSが新しいデータを作る
<li> を append する



actions.push("早起きする");

const li = document.createElement("li");
li.textContent = "早起きする";
list.append(li);



👉 「1件増える」体験はここで作られる


**② 変える（textContent が活きる場面）**

例：進捗表示

progress.textContent = "3 / 5 完了";


データが変わる
表示を「置き換える」

👉 数字・状態表示は全部これ



でも重要な一段上の話（超重要）

ここが本質です。

❌ JS直DOM操作の限界

追加した
消した
書き換えた

…を全部自分で管理する必要がある
→ 壊れやすい


Reactになるとどう変わるか

JS時代（今）
データを変える
→ DOMをどう変えるか考える

React（後半）
データを変える
→ ReactがDOMを勝手に更新する


つまり今日のDOM操作は：

「Reactが裏でやってくれていることの正体」

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

🟦 Day24：DOM更新（変える・増やす）

今日は
「JavaScriptで画面表示をどう変えるか」
をテーマに学習しました。



■ まず超シンプルに言うと…

DOM更新＝人が見ている画面の表示内容を、JavaScriptから変更すること。

HTML：表示される“場所”

JavaScript：表示を変える“命令”

画面：その結果



■ 今日学んだこと

✔ 1) DOM更新には種類がある

DOM操作は細かく見ると色々あるが、
本質は次の2つに集約できると理解した。

変える：textContent
→ 既にある表示内容を置き換える
（例：数字・文章・状態表示）

増やす：append
→ 表示を壊さず、下に追加する
（例：ToDo一覧・Action一覧）


✔ 2) getElement と createElement の役割の違い

getElementById
→ すでに存在しているDOMを取得する

createElement
→ まだ存在しないDOMを新しく作る

「取得」と「生成」を混同するとエラーになる、という実感を得た。


✔ 3) 画面は直接触らないという考え方

人がHTMLを直接書き換えるのではない

JavaScriptがDOMを通して更新する

画面は常に“結果”でしかない

この考え方が
「データが本体、表示は結果」
につながっていると理解した。



■ 出てきた疑問

「これを本番（人生ToDoアプリ）ではどう使うのか？」

勉強用のコードと実際のアプリがどう結びつくのかが疑問だった。



■ 疑問への結論・答え

人生ToDoアプリでは、今日の内容は次の形で使われる。

append
→ Dream / Action / ToDo を一覧として増やす

textContent
→ 進捗、件数、状態などを更新表示する

ただし実務では、
これらのDOM更新は Reactが裏で自動的にやってくれる。

つまり今日学んだDOM操作は、

Reactが内部で行っている処理の正体を理解するための基礎

という位置づけだと整理できた。



■ 今日の一文まとめ（見返し用）

DOM更新とは、
JavaScriptで「表示を変える・増やす」ことであり、
人生ToDoアプリでは一覧表示や進捗更新の土台になる。
Reactではこの処理を自分で書かなくてよくなる。

ここまでで Day24 完了です。