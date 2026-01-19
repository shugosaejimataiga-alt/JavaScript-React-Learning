
## 1.基本の書き方（最小）

書き方は1行だけ

localStorage.getItem("キー名");


**例（昨日保存したものを想定）**

localStorage.setItem("name", "Taro");


これを 取り出す と：

const value = localStorage.getItem("name");
console.log(value);


👉 コンソールには

Taro

と出ます。


**重要ポイント（ここ超大事）**

const value = localStorage.getItem("name");


この value の中身は：

❌ 変数
❌ オブジェクト
❌ 配列

ではなく、

✅ ただの文字列

です。

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

## 2.練習問題（1問だけ）

次のコードを書いたとき、

localStorage.setItem("age", 20);
const age = localStorage.getItem("age");


質問：
age + 1 の結果はどうなりますか？
（数値か／文字列か、結果を書いてください）


解答："201"


ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

流れを1本の線で整理

JavaScriptの配列
↓ JSON.stringify

文字列
↓ localStorage に保存

文字列
↓ localStorage.getItem

文字列
↓ JSON.parse
JavaScriptの配列


ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー


📘 Day31｜localStorage「取得」の完全振り返り
今日のテーマ

localStorage に保存したデータを取り出し、JavaScriptで正しく使える形に戻すこと。



① localStorageの大前提（最重要）

localStorage は 文字列しか保存できない

これは制限であり、仕様

数値・配列・オブジェクトも
👉 保存時に文字列化されている



② 取得の基本構文
localStorage.getItem("キー名");

例：

const value = localStorage.getItem("name");

何を保存していても
👉 戻り値は必ず文字列



③ なぜそのまま使うと事故るのか

localStorage.setItem("age", 20);
const age = localStorage.getItem("age");


このとき：

age + 1


結果は：

"201"


理由：

age は "20"（文字列）

+ は文字列連結になる



④ JSON.stringify / JSON.parse の役割

保存するとき（Day30）

JSON.stringify(配列やオブジェクト)

👉 JavaScriptのデータ → 文字列



取得するとき（Day31）

JSON.parse(文字列)

👉 文字列 → JavaScriptのデータ構造



⑤ 完全な流れ（ここが核心）

JavaScriptの配列
↓ JSON.stringify
文字列
↓ localStorageに保存
文字列
↓ localStorage.getItem
文字列
↓ JSON.parse
JavaScriptの配列



⑥ よくある誤解の整理

❌ JavaScriptのコードに戻る
❌ プログラムとして実行される

ではない。

👉 「データの形」を戻しているだけ



⑦ 実務・Reactにつながる定番形

const todos = JSON.parse(
  localStorage.getItem("todos") || "[]"
);


意味：

localStorage から todos を取り出す
無かったら 空配列として扱う
結果を todos という JSの配列 にする


🔑 Day31の最終結論（1文）

localStorageから取得した値は必ず文字列なので、配列やオブジェクトとして使うには JSON.parse でJavaScriptのデータ構造に戻す必要がある。