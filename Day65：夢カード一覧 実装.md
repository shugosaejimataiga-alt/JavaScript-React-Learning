

🟢 Day65 本質まとめ（完全復元用）


① 今日やったこと

「夢一覧を表示する仕組み」を作った。

やったことは4つ。



② Reactの構造を再確認

Reactは：

データを書く
↓
mapで1個ずつ取り出す
↓
コンポーネントに変換する
↓
returnで画面に出す
③ データ
const dreams = [
  { id: 1, title: "...", detail: "..." }
];

今は固定データ

useStateはまだ使っていない

表示するだけだから不要

理解ポイント：
useStateは「変更する時」に使う



④ mapの本質

dreams.map((dream) => ...)

mapは：

配列を1個ずつ取り出して
別の形に変換する

今回は：

データ → UI部品

に変換した。

理解ポイント：

配列が3個 → DreamCard3回

配列が100個 → DreamCard100回

配列が空 → 0回呼ばれる



⑤ DreamCardの正体

function DreamCard(props) {
  return (...)
}

理解ポイント：

コンポーネントはただの関数

<DreamCard /> は関数呼び出し

propsは引数

returnしたものが画面になる

裏側では：

DreamCard({ title: "...", detail: "..." })

が呼ばれている。



⑥ returnの意味

Reactでは：

returnの中身 = 画面

useStateはデータ

returnは表示

この役割は絶対に混同しない。



⑦ 条件分岐

dreams.length === 0 ? ...

理解ポイント：

空配列 → lengthは0

null → エラー

mapは配列専用



⑧ 今日一番重要な理解

Reactは：

データの数 = UIの数

そして

データをUIに変換する仕組み

である。



⑨ 今の到達レベル

あなたは今：

一覧表示が作れる

コンポーネント分割ができる

条件表示ができる

mapの本質を理解している

これはReact初級を超えています。



Day65：夢カード一覧 実装をしました。