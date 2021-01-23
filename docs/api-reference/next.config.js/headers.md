---
description: Next.js アプリに独自の HTTP ヘッダーを追加します。
---

# ヘッダー

> この機能は [Next.js 9.5](https://nextjs.org/blog/next-9-5) で導入されました。古いバージョンの Next.js をお使いの場合は、アップグレードしてお試しください。

ヘッダーでは、受け取るリクエストパスに対して独自の HTTP ヘッダーを設定できます。

独自の HTTP ヘッダーを設定するためには、 `next.config.js` の `headers` キーを使用します:

```js
module.exports = {
  async headers() {
    return [
      {
        source: '/about',
        headers: [
          {
            key: 'x-custom-header',
            value: 'my custom header value',
          },
          {
            key: 'x-another-custom-header',
            value: 'my other custom header value',
          },
        ],
      },
    ]
  },
}
```

`headers` は非同期関数であり、 `source` と `headers` プロパティを持つオブジェクトが格納された配列を返します:

- `source` は受け取るリクエストパスのパターンです。
- `headers` は `key` と `value` プロパティを持つヘッダーオブジェクトの配列です。

## ヘッダー上書き時の振る舞い

2 つのヘッダーが同じパスにマッチし、同じヘッダーキーが設定されていた場合、最後のヘッダーキーが最初のヘッダーキーを上書きします。以下のヘッダーを使うと、パス `/hello` は最後のヘッダーの値が `world` であるため、ヘッダー `x-hello` の値は `world` となります。


```js
module.exports = {
  async headers() {
    return [
      {
        source: '/:path*',
        headers: [
          {
            key: 'x-hello',
            value: 'there',
          },
        ],
      },
      {
        source: '/hello',
        headers: [
          {
            key: 'x-hello',
            value: 'world',
          },
        ],
      },
    ],
  },
}
```

## パスのマッチング

パスのマッチングができます。例えば、`/blog/:slug` は `/blog/hello-world` とマッチします (ネストされているパスはありません):

```js
module.exports = {
  async headers() {
    return [
      {
        source: '/blog/:slug',
        headers: [
          {
            key: 'x-slug',
            value: ':slug', // マッチしたパラメータを値として使用できます
          },
          {
            key: 'x-slug-:slug', // マッチしたパラメータをキーとして使用できます
            value: 'my other custom header value',
          },
        ],
      },
    ],
  },
}
```

### ワイルドカードを用いたパスのマッチング


ワイルドカードを使ってパスとマッチさせるには、パラメータの後に `*` を使います。例えば、 `/blog/:slug*` は `/blog/a/b/c/d/hello-world` とマッチします:

```js
module.exports = {
  async headers() {
    return [
      {
        source: '/blog/:slug*',
        headers: [
          {
            key: 'x-slug',
            value: ':slug*', // マッチしたパラメータを値として使用できます
          },
          {
            key: 'x-slug-:slug*', // マッチしたパラメータをキーとして使用できます
            value: 'my other custom header value',
          },
        ],
      },
    ],
  },
}
```

### 正規表現を用いたパスのマッチング

パラメータの後に括弧で正規表現を囲むことで、正規表現を用いてパスとマッチさせられます。例えば `/blog/:slug(\d{1,})` は `/blog/123` とマッチしますが、`/blog/abc` とはマッチしません:

```js
module.exports = {
  async headers() {
    return [
      {
        source: '/blog/:post(\\d{1,})',
        headers: [
          {
            key: 'x-post',
            value: ':post',
          },
        ],
      },
    ],
  },
}
```

### basePath をサポートしたヘッダー

ヘッダーで [`basePath` サポート](/docs/api-reference/next.config.js/basepath.md)を利用する際は、ヘッダーに `basePath: false` を追加しない限り、各 `source` に対して自動的に `basePath` がプレフィックスとして付与されます:

```js
module.exports = {
  basePath: '/docs',
  async headers() {
    return [
      {
        source: '/with-basePath', // これは /docs/with-basePath になります
        headers: [
          {
            key: 'x-hello',
            value: 'world',
          },
        ],
      },
      {
        source: '/without-basePath', // basePath: false が設定されているため、変更されません
        headers: [
          {
            key: 'x-hello',
            value: 'world',
          },
        ],
        basePath: false,
      },
    ]
  },
}
```
