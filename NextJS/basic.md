# 基本的な使い方

`create-next-app` でプロジェクトを作成する。

```console
$ npx create-next-app@latest
```

プロジェクトが展開される。

```console
$ tree -I "node_modules"
.
├── app
│   ├── favicon.ico
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
├── next.config.mjs
├── next-env.d.ts
├── package.json
├── package-lock.json
├── postcss.config.mjs
├── public
│   ├── next.svg
│   └── vercel.svg
├── README.md
├── tailwind.config.ts
└── tsconfig.json

3 directories, 14 files
```

このプロジェクト作成は新しくディレクトリを生成して .git も追加したりするのがちょっと使いづらい。

`app` または `src/app` ディレクトリが作成されるが、この階層構造がルーティングに対応している。
ディレクトリ配下の `page.tsx` がそのページのコンポーネントを返す。以下にパスと `page.tsx` の対応例を挙げる。

| パス | ファイルパス |
| --- | --- |
| `/` | `app/page.tsx` |
| `/articles` | `app/articles/page.tsx` |
| `/articles/$articleId` | `app/articles/[articleId]/page.tsx` |

