<!-- textlint-disable -->
# Nextjs-ja-translation-docs
<!-- textlint-enable -->

<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-23-orange.svg?style=flat-square)](#contributors)
<!-- ALL-CONTRIBUTORS-BADGE:END -->

![reviewdog](https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/workflows/reviewdog/badge.svg)

Next.js のドキュメントを翻訳する非公式プロジェクトです。

[本家公式ドキュメント](https://nextjs.org/docs/getting-started)

## 翻訳手順

翻訳の状況は、[翻訳の概要と進捗状況](https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/issues/3)の issues を確認してください。

### 手順1:翻訳を始める準備

まずは、このリポジトリを右上から Fork してください。

そして、リポジトリをクローンします。`your`には、あなたの GitHub のユーザーネームを入れてください。

```
$ git clone https://github.com/your/Nextjs-ja-translation-docs
$ cd Nextjs-ja-translation-docs
```

dependency のインストールをしてください。必ず `yarn` で行ってください。

```
$ yarn install
```

開発サーバーが無事に起動するか確認してください。

```
$ yarn dev
```

翻訳作業を行うためのブランチを作成します。ここでは、例として `docs/example.md` を翻訳するためのブランチを作成します。

```
$ git checkout -b docs/example
```

これで、翻訳を始める準備は完了です。エディタを使って、翻訳箇所のファイルを編集します。

また、docs/manifest.json の各セクションのタイトルが設定されています。自分の担当箇所のタイトルを翻訳してください。

getting-started を翻訳する例:

```
{ "title": "はじめに", "path": "/docs/getting-started.md" },
```

### 手順2:翻訳完了からプルリクエスト

precommit 時に翻訳の対象ファイルに対して textlint が走ります。textlint が通らない限り commit できません。エラーを修正する場合は、`text-lint:fix`を使います。

```
$ yarn text-lint:fix ./docs/example.md
```

翻訳箇所をコミットしてプッシュします。コミットはできるだけ 1 つにまとめてください。

```
$ git add .
$ git commit -m "docs: translate docs/example.md"
$ git push -u origin docs/example.md
```

最後に、GitHub 上からプルリクエストを作成してください。その後、メンテナーがレビューをして問題がなければマージされます。

## Q&A

質問がある場合は、[Slack](https://join.slack.com/t/nextjs-ja/shared_invite/zt-f9knbi69-AjTZqNZpYv7knG30jPwHcQ)に参加して、#questions チャンネルまでお願いします。

## Contributors ✨

Thanks to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://shinyaigeek.dev/"><img src="https://avatars1.githubusercontent.com/u/42742053?v=4" width="100px;" alt=""/><br /><sub><b>Shinobu Hayashi</b></sub></a><br /><a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/commits?author=Shinyaigeek" title="Code">💻</a> <a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/pulls?q=is%3Apr+reviewed-by%3AShinyaigeek" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="https://code-log.hatenablog.com/"><img src="https://avatars0.githubusercontent.com/u/39504660?v=4" width="100px;" alt=""/><br /><sub><b>かみむら</b></sub></a><br /><a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/commits?author=hiro08gh" title="Code">💻</a> <a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/pulls?q=is%3Apr+reviewed-by%3Ahiro08gh" title="Reviewed Pull Requests">👀</a> <a href="#translation-hiro08gh" title="Translation">🌍</a></td>
    <td align="center"><a href="https://github.com/hoosan"><img src="https://avatars3.githubusercontent.com/u/40290137?v=4" width="100px;" alt=""/><br /><sub><b>hoosan</b></sub></a><br /><a href="#translation-hoosan" title="Translation">🌍</a> <a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/commits?author=hoosan" title="Documentation">📖</a> <a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/pulls?q=is%3Apr+reviewed-by%3Ahoosan" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="https://twitter.com/okumura_daiki"><img src="https://avatars3.githubusercontent.com/u/4679138?v=4" width="100px;" alt=""/><br /><sub><b>Daiki Okumura</b></sub></a><br /><a href="#translation-okmr-d" title="Translation">🌍</a></td>
    <td align="center"><a href="https://about.me/yokinist"><img src="https://avatars2.githubusercontent.com/u/19779874?v=4" width="100px;" alt=""/><br /><sub><b>yokinist</b></sub></a><br /><a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/commits?author=yokinist" title="Documentation">📖</a> <a href="#translation-yokinist" title="Translation">🌍</a> <a href="#tool-yokinist" title="Tools">🔧</a> <a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/pulls?q=is%3Apr+reviewed-by%3Ayokinist" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="https://github.com/96-38"><img src="https://avatars1.githubusercontent.com/u/48713768?v=4" width="100px;" alt=""/><br /><sub><b>kurosawa</b></sub></a><br /><a href="#translation-96-38" title="Translation">🌍</a></td>
    <td align="center"><a href="http://www.facebook.com/noriaki.uchiyama"><img src="https://avatars3.githubusercontent.com/u/44050?v=4" width="100px;" alt=""/><br /><sub><b>Noriaki UCHIYAMA</b></sub></a><br /><a href="#translation-noriaki" title="Translation">🌍</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://ria-blog.org"><img src="https://avatars2.githubusercontent.com/u/11747541?v=4" width="100px;" alt=""/><br /><sub><b>ria</b></sub></a><br /><a href="#translation-ria3100" title="Translation">🌍</a></td>
    <td align="center"><a href="https://peaceful-mcclintock-c87ee2.netlify.app/"><img src="https://avatars0.githubusercontent.com/u/36391432?v=4" width="100px;" alt=""/><br /><sub><b>ryuckel</b></sub></a><br /><a href="#translation-ryuckel" title="Translation">🌍</a></td>
    <td align="center"><a href="https://yamanoku.net"><img src="https://avatars1.githubusercontent.com/u/1996642?v=4" width="100px;" alt=""/><br /><sub><b>Okuto Oyama</b></sub></a><br /><a href="#translation-yamanoku" title="Translation">🌍</a></td>
    <td align="center"><a href="https://github.com/syakoo"><img src="https://avatars1.githubusercontent.com/u/12678450?v=4" width="100px;" alt=""/><br /><sub><b>syakoo</b></sub></a><br /><a href="#translation-syakoo" title="Translation">🌍</a></td>
    <td align="center"><a href="https://thesugar.me"><img src="https://avatars1.githubusercontent.com/u/53966025?v=4" width="100px;" alt=""/><br /><sub><b>thesugar / Ryohei Sato</b></sub></a><br /><a href="https://github.com/Nextjs-ja-translation/Nextjs-ja-translation-docs/pulls?q=is%3Apr+reviewed-by%3Athesugar" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a href="http://queq1890.info"><img src="https://avatars2.githubusercontent.com/u/32263803?v=4" width="100px;" alt=""/><br /><sub><b>Yuji Matsumoto</b></sub></a><br /><a href="#translation-queq1890" title="Translation">🌍</a></td>
    <td align="center"><a href="https://github.com/mpg-teruhisa-fukumoto"><img src="https://avatars2.githubusercontent.com/u/21003135?v=4" width="100px;" alt=""/><br /><sub><b>Teruhisa Fukumoto</b></sub></a><br /><a href="#translation-f-teruhisa" title="Translation">🌍</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://twitter.com/takepepe"><img src="https://avatars1.githubusercontent.com/u/22139818?v=4" width="100px;" alt=""/><br /><sub><b>Takefumi Yoshii</b></sub></a><br /><a href="#translation-takefumi-yoshii" title="Translation">🌍</a></td>
    <td align="center"><a href="https://github.com/rikusen0335"><img src="https://avatars0.githubusercontent.com/u/19174234?v=4" width="100px;" alt=""/><br /><sub><b>rikusen0335</b></sub></a><br /><a href="#translation-rikusen0335" title="Translation">🌍</a></td>
    <td align="center"><a href="https://github.com/kentaro84207"><img src="https://avatars1.githubusercontent.com/u/33363411?v=4" width="100px;" alt=""/><br /><sub><b>Kentaro Suzuki</b></sub></a><br /><a href="#translation-kentaro84207" title="Translation">🌍</a></td>
    <td align="center"><a href="https://github.com/ogugu9"><img src="https://avatars1.githubusercontent.com/u/14102616?v=4" width="100px;" alt=""/><br /><sub><b>ogugu</b></sub></a><br /><a href="#translation-ogugu9" title="Translation">🌍</a></td>
    <td align="center"><a href="https://mottox2.com"><img src="https://avatars3.githubusercontent.com/u/7007253?v=4" width="100px;" alt=""/><br /><sub><b>Yuki Takemoto</b></sub></a><br /><a href="#translation-mottox2" title="Translation">🌍</a></td>
    <td align="center"><a href="http://qiita.com/ossan-engineer"><img src="https://avatars0.githubusercontent.com/u/2215105?v=4" width="100px;" alt=""/><br /><sub><b>Kiichi Tachibana</b></sub></a><br /><a href="#translation-ossan-engineer" title="Translation">🌍</a></td>
    <td align="center"><a href="https://github.com/resqnet"><img src="https://avatars3.githubusercontent.com/u/12475586?v=4" width="100px;" alt=""/><br /><sub><b>ken_o</b></sub></a><br /><a href="#translation-resqnet" title="Translation">🌍</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://panda-program.com/"><img src="https://avatars0.githubusercontent.com/u/36080801?v=4" width="100px;" alt=""/><br /><sub><b>Mashu Kushibiki</b></sub></a><br /><a href="#translation-KushibikiMashu" title="Translation">🌍</a></td>
    <td align="center"><a href="https://yopinoji.com/"><img src="https://avatars0.githubusercontent.com/u/46310104?v=4" width="100px;" alt=""/><br /><sub><b>Masaki Yoshiiwa</b></sub></a><br /><a href="#translation-YopiNoji" title="Translation">🌍</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->
