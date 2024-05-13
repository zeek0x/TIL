# Hydration Error

Hydration Error とはSSR（サーバサイドレンダリング）の結果とクライアントサイドのReactコンポーネントの状態が一致しない場合に発生するエラーを指す。
Hydration とは、水和・加水を意味しており、Web開発においてサーバから送られた静的なHTMLにクライアントサイドのJavaScriptによって対話機能を足していく様子を表している。

一般的には、SSRの結果と React コンポーネントの状態を揃えることで解決するべきである。
しかし、時刻表示やなど、本質的に複数回のレンダリングで一意に定めることができない場合は `suppressHydrationWarning` を指定してエラーを無視することができる。

- エラーの例

```
Unhandled Runtime Error
Error: Text content does not match server-rendered HTML.
See more info here: https://nextjs.org/docs/messages/react-hydration-error

Text content did not match. Server: "2024-05-13 13:08:24.547" Client: "2024-05-13 22:08:25.176"


<Home>
  <main>
    <h1>
      "2024-05-13 13:08:24.547"
      "2024-05-13 22:08:25.176"
```

- `suppressHydrationWarning` を指定する例

```
    <main className="h-screen w-screen flex justify-center items-center">
      <h1
        className="text-9xl font-bold tabular-nums"
        suppressHydrationWarning={true}
      >
        {format(date)}
      </h1>
    </main>
```
