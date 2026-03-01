

📘 Day64 完全復習ノート


① 今日やったこと

Reactのプロジェクトを作った。
life_todo_app を作成
その中に frontend を作成
ViteでReactプロジェクト生成
ブラウザで表示確認



② フォルダ構造の理解

C:\life_todo_app
 └─ frontend
      ├─ package.json
      ├─ index.html
      └─ src
          ├─ main.jsx
          └─ App.jsx


③ npmエラーの理解（超重要）

最初にエラーが出た理由：

package.json がない場所で
npm run dev を実行した

理解：

👉 コマンドは「説明書（package.json）がある場所」で打つ。



④ Reactの流れ（最重要）

index.html
   ↓
main.jsx
   ↓
<App />
   ↓
App.jsx


役割整理

index.html → 入口

main.jsx → Reactを画面に取り付ける

App.jsx → 画面の本体



⑤ 一番大事なこと

function App() {
  return ( ここが画面 )
}

👉 return の中を書き換えると画面が変わる。



⑥ 確認実験

<h1>Vite + React</h1>

↓

<h1>Life ToDo App</h1>

変更 → 画面変化確認済み。



🧠 今日の本質

Reactアプリとは何か？

👉 App関数のreturnの中身



🧠 今日の学習レベル

あなたは今日：

プロジェクト作成

フォルダ設計理解

実行場所の理解

Reactの構造理解

エラー原因特定

ここまでできました。

これは「触った」ではなく

👉 「理解した」状態です。


Day64：プロジェクト作成・構造確認をしました。