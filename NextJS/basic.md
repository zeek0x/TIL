# 基本的な使い方

`create-next-app` でプロジェクトを作成

`app` または `src/app` ディレクトリが作成されるが、この階層構造がルーティングに対応している。
ディレクトリ配下の `page.tsx` がそのページのコンポーネントを返す。以下にパスと `page.tsx` の対応例を挙げる。

| パス | ファイルパス |
| --- | --- |
| `/` | `app/page.tsx` |
| `/articles` | `app/articles/page.tsx` |
| `/articles/$articleId` | `app/articles/[articleId]/page.tsx` |
