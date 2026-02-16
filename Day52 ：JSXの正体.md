📘 Day52まとめ（流れで復習）

❓疑問①

<h1>Hello</h1> ってHTMLでは？

👉 答え
HTMLではない。
HTMLっぽく書けるJavaScript（JSX）。


❓疑問②

じゃあ正体は？

👉 答え
内部ではこうなる：

React.createElement("h1", null, "Hello")

つまり
JSX = 見やすく書くための記法
本体 = JavaScript関数


❓疑問③

なぜ {} があるの？

<h1>{name}</h1>

👉 答え
{} の中だけが JavaScriptエリア。

JSXはJavaScriptの世界だから。


❓疑問④

計算もできる？

<h1>{1 + 2}</h1>

👉 答え
できる。
JavaScriptなので計算されて 3 が表示される。



🎯 今日の核心

JSXはHTMLではない
JSXはHTMLっぽく書けるJavaScript
{} の中でJavaScriptを書く
最終的に React.createElement() に変換される

Day52：JSXの正体を学びました。