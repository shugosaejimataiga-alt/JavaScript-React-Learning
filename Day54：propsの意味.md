完全版まとめ（最終形）

🔵 Reactは3つだけ

① コンポーネント
② JSX
③ props



① コンポーネント

👉 ただの関数

function Profile(props) {
  return <p>{props.name}</p>;
}


② JSX

👉 HTMLっぽく書けるJavaScript構文

<Profile name="Taro" />

これは内部で：

React.createElement(Profile, { name: "Taro" })

になり、最終的に

Profile({ name: "Taro" })

が実行される。



③ props

👉 Reactがコンポーネントを実行するときに渡す
👉 オブジェクト型の引数



🧠 最終超シンプル図

コンポーネント ＝ 関数
JSX ＝ 呼び出しの見た目
props ＝ 渡される引数