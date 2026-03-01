

📘 Day62 完全まとめ
「人生ToDoアプリをReactで分解する」



① コンポーネントの正体

コンポーネント = 関数

return は UI（JSX）を返す

データを親に返す仕組みではない

👉 ここが最大の誤解ポイントだった



② コンポーネントの役割分離

ページ（状態を持つ）

DreamListPage
ActionListPage


部品（表示専用）

DreamCard
ActionCard


入力担当（追加依頼）

AddDreamPage
AddActionPage



③ 状態の原則

状態は「一覧を持つ側」に置く

子は基本的に状態を持たない

管理者は1人にする

例：

const [dreams, setDreams] = useState([]);

は DreamListPage に置く。



④ データの流れ（Reactの本質）

上 → 下
データ（props）

下 → 上
親から渡された関数を実行

重要：

子は return で親にデータを渡さない

子は「親の関数を実行する」だけ



⑤ 追加処理の仕組み

親：

<AddDreamPage addDream={addDream} />


子：

props.addDream(newDream);


つまり：

子は dreams を直接変更しない

親に「追加して」と依頼する



⑥ dreamsのデータ構造

複数ある → 配列

1つの夢 → オブジェクト

idで識別（位置では管理しない）

例：

[
  { id: 1, title: "海外で働く" },
  { id: 2, title: "アプリ完成" }
]



🔥 今日の核心まとめ（1文）

Reactは

「状態は上、表示は下、変更は関数で依頼」

で動く。