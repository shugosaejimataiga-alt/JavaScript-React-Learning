📘 Day66まとめ（React：Action追加の完全理解）


🎯 今日の本質テーマ

「入力 → 追加 → 再描画」の流れを完全理解する

🟢 ① データの始まり（App）
const dreams = [
  {
    id: 1,
    title: "エンジニアになる",
    detail: "ITで働く",
    actions: [
      { id: 1, text: "毎日1時間勉強" }
    ]
  }
];

dreams はただの配列

DreamCard に props として渡す



🟢 ② <DreamCard /> は関数呼び出し
<DreamCard
  title={dream.title}
  detail={dream.detail}
  actions={dream.actions}
/>

これは実質：

DreamCard({ ... })

props にデータが入る



🟢 ③ DreamCardの中で起きること
const [actions, setActions] = useState(props.actions);
const [inputText, setInputText] = useState("");

props.actions を state にコピー

inputText は入力用のstate

title / detail は props のまま



🟢 ④ 表示の流れ
{actions.map((action) => (
  <p key={action.id}>{action.text}</p>
))}

actions の中身を分解して表示

state が変われば再描画



🟢 ⑤ 入力の流れ
<input
  value={inputText}
  onChange={(e) => setInputText(e.target.value)}
/>

流れ：

入力する
→ onChange 発動
→ setInputText
→ 再描画
→ value に反映

⚠ 入力中は actions は変わらない



🟢 ⑥ 追加の流れ
<button onClick={handleAdd}>

ボタン押す
→ handleAdd 実行



🟢 ⑦ handleAddの中身
if (inputText === "") return;

const newAction = {
  id: actions.length + 1,
  text: inputText
};

setActions([...actions, newAction]);
setInputText("");



重要ポイント：

空なら終了

newAction を作る

既存配列に「足す」のではない

新しい配列を作る

setActions が呼ばれた瞬間に再描画

入力欄は空に戻る




🔥 今日の核心理解
Reactは

「stateの箱（参照）が変わったら再描画」

だけ。

追加とは

既存配列を変更することではない。

👉 新しい配列を作ること。

入力と追加は別イベント

入力 → onChange

追加 → onClick

混ざらない。