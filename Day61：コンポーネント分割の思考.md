

🟦 Day61：コンポーネント分割の思考（完全整理）



① コンポーネント分割の本質

Reactでは

1コンポーネント = 1つの役割

巨大な1ファイルに全部書くと：

stateが増えすぎる
責任が混ざる
修正が怖くなる
バグが見つけにくい

だから分ける。



② 親と子の役割

🔹 親

データ（state）を持つ
並べる
全体を管理する


🔹 子

propsを受け取る
表示に集中する
操作ボタンを置く



③ stateとは何か

state = 変わるデータ

例：

夢の配列
完了フラグ
入力中の文字
カウント数
変わるものはstate。



④ 子にstateを持たせすぎると何が起きる？

親が把握できない
保存できない
並び替えできない
完了数を集計できない
管理不能になる

だから基本ルール：

全体に関わるstateは親が持つ



⑤ stateを持ち上げる（Lifting State Up）

もし複数の部品で同じデータを使うなら：

App
 ├── Header
 └── DreamList

Headerでも使うなら、

dreamsはどこに置く？

👉 共通の親である App



⑥ stateの置き場所の決め方（超重要）

stateは「それを使う範囲の一番近い親」に置く

例

DreamListだけで使う → DreamListに置く

Headerでも使う → Appに持ち上げる

1枚だけの見た目 → propsで渡す（stateにしない）



⑦ 人生ToDoアプリ構造（現時点）
App
 ├── Header
 └── DreamList
       ├── DreamAddForm
       └── DreamCard

dreams配列 → DreamList（or App※共有するなら）

DreamCardは表示のみ

DreamAddFormは追加のみ



🎯 今日の最重要1行

stateは「それを使う範囲の一番近い親」に置く

Day61：コンポーネント分割の思考を学びました。