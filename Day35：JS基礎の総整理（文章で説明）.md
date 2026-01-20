🟦 Day35｜JS基礎・完全整理まとめ


■ 今日のテーマ

JavaScriptで今まで何をしていたのかを、一本の流れで固定する


■ 結論（最重要）

データが本体。
画面（DOM）はデータの結果。

JavaScriptの役割は
👉 DOM操作によって、画面をデータ通りにすること



■ 今日学んだこと（流れで整理）

① 状態（データ）がある

let todos = [];

アプリの本体
正解の世界



② ユーザー操作で状態を変える

todos.push(text);

データだけを変更
ここでは画面は触らない



③ render() を呼ぶ

render();

状態変更後に必ず呼ぶ
画面更新の合図



④ renderの中でDOM操作する

const ul = document.getElementById("list");
ul.innerHTML = "";

HTMLを取得
一旦すべて消す


for (const todo of todos) {
  const li = document.createElement("li");
  li.textContent = todo;
  ul.appendChild(li);
}

データを1つずつ取り出す
DOMを作り直す

👉 DOM操作は render の中だけ



■ render() の正体

❌ よくある誤解

render = リロード
ページ再読み込み
サーバー通信


✅ 正しい理解

render = 画面を書き直す関数

同じページのまま
データを見てDOMを再生成するだけ



■ 今日出た疑問と答え


Q1. render()って再描画？リロード？

A. 再描画。リロードではない。

再描画：DOMを書き直す

リロード：ページ自体を再起動する


Q2. render()を呼ばないとどうなる？

A. データと画面がズレる。

状態：正しい

画面：古いまま

👉 UIが壊れる原因


Q3. なぜDOMを直接操作すると辛い？

A. データと画面の整合性が崩れるから。

DOMは結果でしかない

本体（データ）を無視すると事故る



■ 今日の最重要フレーズ（暗記用）

状態を変えたら、必ず render()

DOM操作は render の中だけ

renderは画面更新、リロードではない

画面をデータ通りにする関数＝render



■ Reactとのつながり（予告）

今日まで：

状態変更 → render()


React：

状態変更 → Reactが自動でrender


👉 Reactは「renderを自動化したJS」

これで Day35は完全固定です。