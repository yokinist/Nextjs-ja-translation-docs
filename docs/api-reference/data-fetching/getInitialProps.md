---
description: getInitialProps を使い、ページでサーバーサイドレンダリングを有効にして初期データを追加します。
---

# getInitialProps

>**推奨: [`getStaticProps`](/docs/basic-features/data-fetching.md#getstaticprops-static-generation) または [`getServerSideProps`](/docs/basic-features/data-fetching.md#getserversideprops-server-side-rendering)**
>
> Next.js 9.3以降を使用している場合は、 `getInitialProps` ではなく、 `getStaticProps` または `getServerSideProps` を使用することをお勧めします。
>
> これらの新しいデータ取得メソッドを使用することで、静的生成とサーバーサイドレンダリングを細かく選択できるようになります。
> [Pages](/docs/basic-features/pages.md) と[データ取得](/docs/basic-features/data-fetching.md)のドキュメントの詳細については、こちらをご覧ください:

<details>
  <summary><b>例</b></summary>
  <ul>
    <li><a href="https://github.com/vercel/next.js/tree/canary/examples/data-fetch">Data fetch</a></li>
  </ul>
</details>

  `getInitialProps` は、ページ内の[サーバーサイドレンダリング](/docs/basic-features/pages.md#server-side-rendering
)を可能にし、初期データを追加出来るようになります。つまり、既にデータが追加されているページをサーバーから送信するということです。これは特に [SEO](https://ja.wikipedia.org/wiki/%E6%A4%9C%E7%B4%A2%E3%82%A8%E3%83%B3%E3%82%B8%E3%83%B3%E6%9C%80%E9%81%A9%E5%8C%96) 対策に有効です。

> `getInitialProps` は [Automatic Static Optimization](/docs/advanced-features/automatic-static-optimization.md) を無効化します。

`getInitialProps` は、任意のページに[`静的メソッド`](https://ja.javascript.info/static-properties-methods)として追加できる[`非同期`](https://vercel.com/blog/async-and-await) 関数です。次の例を見てみましょう:

```jsx
function Page({ stars }) {
  return <div>Next stars: {stars}</div>;
}

Page.getInitialProps = async ctx => {
  const res = await fetch('https://api.github.com/repos/zeit/next.js');
  const json = await res.json();
  return { stars: json.stargazers_count };
};

export default Page;
```

もしくは、クラスコンポーネントを使って以下のように書くこともできます:

```jsx
import React from 'react';

class Page extends React.Component {
  static async getInitialProps(ctx) {
    const res = await fetch('https://api.github.com/repos/zeit/next.js');
    const json = await res.json();
    return { stars: json.stargazers_count };
  }

  render() {
    return <div>Next stars: {this.props.stars}</div>;
  }
}

export default Page;
```

`getInitialProps` は非同期にデータを取得して `props` にデータを追加するために使われます。

`getInitialProps` から返されるデータは、 [`JSON.stringify`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) が行うのと同じように、サーバーレンダリング時にシリアライズされます。 `getInitialProps` から返されるオブジェクトがプレーンなオブジェクトで `Date` 、 `Map` 、 `Set` を使用していないことを確認してください。

最初のページのロードでは、 `getInitialProps` はサーバー上でのみ実行されます。
`getInitialProps` は、 [`next/link`](/docs/api-reference/next/link.md) コンポーネントを介して、または [`next/router`](/docs/api-reference/next/router.md) を使用して別のルートへ移動するときにクライアント上で実行されます。

## Context オブジェクト

`getInitialProps` は `context` という単一の引数を受け取り、この `context` は以下のプロパティを持つオブジェクトです:

- `pathname` - 現在のルート。これは /pages にあるページのパスです。
- `query` - オブジェクトとしてパース(解析)される URL のクエリ文字列セクションです。
- `asPath` - ブラウザに表示される実際のパスの文字列です(クエリを含む)。
- `req` - HTTP リクエストオブジェクトです(サーバのみ)。
- `res` - HTTP レスポンスオブジェクトです(サーバのみ)。
- `err` - レンダリング中にエラーが発生した場合のエラーオブジェクトです。

## 注意事項

- `getInitialProps` は各ページの export 部分のみで使用できます。子コンポーネントでは使用**できません**。
- `getInitialProps` の中でサーバーサイドのみのモジュールを使用している場合は、[それらを適切にインポート](https://arunoda.me/blog/ssr-and-server-only-modules)するようにしてください。そうしなければアプリが遅くなってしまうでしょう。

## TypeScript

もし TypeScript を使っているならば、関数コンポーネントに `NextPage` 型を使用できます:

```jsx
import { NextPage } from 'next';

interface Props {
  userAgent?: string;
}

const Page: NextPage<Props> = ({ userAgent }) => <main>Your user agent: {userAgent}</main>;

Page.getInitialProps = async ({ req }) => {
  const userAgent = req ? req.headers['user-agent'] : navigator.userAgent;
  return { userAgent };
};

export default Page;
```

`React.Component` には、 `NextPageContext` を使用できます:

```jsx
import React from 'react';
import { NextPageContext } from 'next';

interface Props {
  userAgent?: string;
}

export default class Page extends React.Component<Props> {
  static async getInitialProps({ req }: NextPageContext) {
    const userAgent = req ? req.headers['user-agent'] : navigator.userAgent;
    return { userAgent };
  }

  render() {
    const { userAgent } = this.props;
    return <main>Your user agent: {userAgent}</main>;
  }
}
```

## 関連事項

次にやるべきこととして、以下のセクションを読むことをお勧めします:

<div class="card">
  <a href="/docs/basic-features/data-fetching.md">
    <b>データ取得:</b>
    <small>Next.js のデータ取得について詳しく学びましょう。</small>
  </a>
</div>

<div class="card">
  <a href="/docs/basic-features/pages.md">
    <b>Pages:</b>
    <small>Next.js の pages について詳しく学びましょう。</small>
  </a>
</div>

<div class="card">
  <a href="/docs/advanced-features/automatic-static-optimization.md">
    <b>Automatic Static Optimization:</b>
    <small>Next.js の Automatic Static Optimization について詳しく学びましょう。</small>
  </a>
</div>
