


🟦 Day58 完全整理ノート


① コンポーネントは永遠ではない

Reactコンポーネントには流れがある。

mount（生まれる）

update（更新される）

unmount（消える）

これを ライフサイクル という。



② useState の本質

const [count, setCount] = useState(0);

count → 今の状態（データ）
setCount → 状態を変更する関数

setCount を呼ぶと React に通知 → 再描画

普通の変数では再描画されない。



③ useEffect の本質

useEffect は

👉 画面そのものではない処理を書く場所

例：

API通信
タイマー
localStorage保存
イベント登録



④ useEffect とライフサイクル

useEffect(() => {
  // マウント時の処理

  return () => {
    // アンマウント時の後片付け
  };
}, []);

空配列 [] → マウント時に1回

return の中 → アンマウント時



⑤ なぜアンマウント処理が必要？

例：

const id = setInterval(...);

return () => {
  clearInterval(id);
};

止めないと：

タイマーが動き続ける
メモリリークになる

👉 消えるときは「後片付け」が必要。



⑥ useEffect と状態の関係

useEffect(() => {
  localStorage.setItem("count", count);
}, [count]);

流れ：

setCountで状態変更

再描画

countが変わった

useEffectが実行

ローカルストレージ保存

"count" → 保存名
count → 今の状態の値



🧠 今日の核心

useState → データそのもの

useEffect → データ変化による外部処理（副作用）

コンポーネントは永遠ではない

だからライフサイクルを意識する



🎯 最重要一文

コンポーネントは永遠に存在しないため、
生まれる・更新される・消えるタイミングごとに処理を分ける必要がある。

Day58：ライフサイクル概念を学びました。