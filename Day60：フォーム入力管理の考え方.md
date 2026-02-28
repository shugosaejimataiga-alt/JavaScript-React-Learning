

🟦 Day60 完全まとめ
フォーム入力管理（Controlled Component）


① 今日の核心

入力欄の中身は DOM に任せない
state で管理する

これが Controlled Component



② なぜそうする？

Reactの原則：

データが本体、表示は結果

inputの中身をDOMに任せると
Reactが把握できない。

だから：

入力値 ＝ state

にする。



③ 基本コード

const [name, setName] = useState("");

<input
  value={name}
  onChange={(e) => setName(e.target.value)}
/>

<p>{name}</p>


④ それぞれの意味

🔹 value={name}
→ 入力欄の表示は state が決める

🔹 onChange={(e) => setName(e.target.value)}
→ 入力されたら state を更新する

🔹 e.target.value
e → イベント情報
target → 今触った input
value → 入力欄の中の文字

つまり：

今入力されている文字



⑤ 流れ（超重要）

① 入力する（Shu）
② onChangeが発火
③ setName("Shu") 実行
④ name が "Shu" になる
⑤ 再描画
⑥ <p>{name}</p> に Shu が表示される



⑥ 重要な誤解ポイント

❌ これは代入ではない
onChange={(e) => setName(e.target.value)}

は

onChange に関数を登録しているだけ



❌ 順番は関係ない

value={name}
onChange={...}

はただの「設定一覧」



⑦ set関数の本当の役割

setName("Shu") は：

① stateを更新する
② Reactに通知する
③ 再描画させる

「通知だけ」ではない。



🎯 今日の本質を一文で

入力欄は state の表示装置である


Day60：フォーム入力管理の考え方を学びました。