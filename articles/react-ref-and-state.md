---
title: "React の useState と useRef の使い分け"
emoji: "🤖"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["react"]
published: true
---

# React の useState と useRef 

Reactの`useState`と`useRef`について簡単に違いをまとめてみました。

## モチベーション

初学者の方だと、Reactにおいて、可変な値を管理するのには useState を使うと考えている人が多いと思います。なぜなら、チュートリアル等で最初に出てくる、useStateを使わないReactの実装はないといっても過言ではないからです。
しかし、ある日を堺に useRef を使いたいと思うときが来ます。そんな時が来たときのために、その取っ掛かりとしてこの記事は書きました。

## `useState`と`useRef` の比較

まず、結論として簡単な違いを以下にまとめます。

| 特徴               | `useState`               | `useRef`                 |
| ------------------ | ------------------------ | ------------------------ |
| **目的**           | コンポーネントの状態管理 | 可変値の保存             |
| **再レンダリング** | 状態が変化したときに発生 | 値が変化しても発生しない |
| **使用例**         | カウンター、フォーム入力 | DOM参照、タイマー        |


特に注目するところは、`再レンダリング` です。ずばり、前述で述べた`ある日`というのは、React の内部で可変な値を管理したいのだけれども、コンポーネントを再レンダリングさせたくない時になります。


## `useState` の例

これはチュートリアルにもあるようなよくある `useState`の使い方例です。以下の場合、`count` を増やしていくたびに、UI に反映させたいです。そのため、`useState`を使うべきです。

### 例:

```javascript
const [count, setCount] = React.useState(0);

const increment = () => setCount(count + 1);

return (
  <div>
    <p>Count: {count}</p>
    <button onClick={increment}>Increment</button>
  </div>
);
```

---

## `useRef` の例

`useRef`は前述のとおり、再レンダリングなしで保持される可変値を保存することができます。この点が`useState`とは異なります。`useRef`にはどんな値でも保存できますが、DOM要素の参照を保存するのがよくある使い方です。
この例では、`inputRef`は`input`要素の参照を保持しています。この場合、`useState` を使ってinputの値を管理しようとすると、input が変化するたびにレンダリングが発生してしまいます。これはパフォーマンスの観点からはあまり良くありません。

### 例:

```javascript
  const inputRef = React.useRef(null);

  const getInputValue = () => {
    if (inputRef.current) {
      console.log(`Input Value: ${inputRef.current.value}`);
    }
  };

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={getInputValue}>Get Input Value</button>
    </div>
  );

```

`useState` の例

```javascript
 const [inputValue, setInputValue] = useState('');

  const handleInputChange = (event) => {
    setInputValue(event.target.value);
  };

  const showInputValue = () => {
    alert(`Input Value: ${inputValue}`);
  };

  return (
    <div>
      <input
        type="text"
        value={inputValue}
        onChange={handleInputChange}
      />
      <button onClick={showInputValue}>Get Input Value</button>
    </div>
  );
};
```

## よくある間違いと解決策

よくある間違いとというか、自分がしてしまった間違いを列挙してみます。

### 依存配列に`ref.current`を含める

`useEffect`フックの依存配列に`ref.current`を追加するのは不要であり、問題を引き起こす可能性があります。`ref.current`の更新は再レンダリングを引き起こさないため、Reactは値が変化したことを認識しません。

**誤ったコード:**

```javascript
const [errorMessage, setErrorMessage] = useState("")
const usernameInputRef = useRef()

React.useEffect(() => {
  setErrorMessage(`${usernameInputRef.current}は不正な値です`)
}, [errorMessage, usernameInputRef.current]); 
```

**解決策:**

1. `ref.current`を依存配列から削除します。
2. 値の変化に応じてエフェクトを実行する必要がある場合は、`useState`を使用します。

```javascript
 const [errorMessage, setErrorMessage] = useState('');
  const [username, setUsername] = useState(''); // 状態で値を管理
  const usernameInputRef = useRef();

  const validateUsername = () => {
    if (username.length < 3) {
      setErrorMessage(`${username}は短すぎます`);
    } else {
      setErrorMessage(''); 
    }
  };

  useEffect(() => {
    validateUsername(); // username の変化時に検証
  }, [username]);

  const handleInputChange = () => {
    setUsername(usernameInputRef.current.value);
  };

  return (
    <div>
      <input
        type="text"
        ref={usernameInputRef}
        onChange={handleInputChange} // 入力時に状態を更新
      />
      <p>{errorMessage}</p>
    </div>
  );

```

