

## 1.今回の学習の説明（まず概念だけ）

**async / await は「非同期処理を、上から順に読める形で書くための書き方」**です。

Day45〜46でやったことを思い出してください。

非同期処理：
👉「今すぐ終わらない処理（通信・待ち時間など）」

Promise：
👉「将来結果が返ってくる約束」

問題点
Promise は .then() が増えると、
「流れが見えにくい」「上から下に読めない」

👉 それを解決するのが async / await

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

## 2.基本の書き方（最小セット）

① async は「この関数は非同期ですよ」という宣言

async function loadData() {
}

または

const loadData = async () => {
}



② await は「Promiseが終わるまで待つ」

const result = await somePromise;

意味はこれだけです👇

somePromise が 終わるまで待つ
終わった結果を result に入れる
見た目は「普通の代入」

⚠️ await は async の中でしか使えない



③ Promise + await の対応関係（超重要）

// Promise版
fetchData().then(data => {
  console.log(data);
});


⬇️ async / await版

const data = await fetchData();
console.log(data);


👉 やってることは同じ
👉 書き方だけが違う

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

