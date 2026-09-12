# MachiVerse Content

MachiVerse公式Webサイトなどから参照する、公開コンテンツ配信用リポジトリです。

## 公開ディレクトリ

GitHub Pagesでは、リポジトリ直下の `root/` を公開ルートとして配信します。

- `root/feeds/mio-devlog.json` — MIO DEVLOG / 南雲の開発日記
- `root/feeds/world-feed.json` — 公式インスタンス向け WORLD FEED
- `root/index.json` — 公開フィードのマニフェスト

公開URL:

- `https://content.machiverse.app/feeds/mio-devlog.json`
- `https://content.machiverse.app/feeds/world-feed.json`
- `https://content.machiverse.app/index.json`

## 更新方針

投稿データの通常更新は `root/feeds/` 配下のJSONだけを編集します。Webサイト側の表示ロジック・CSSは `MachiVerse-Website` で管理します。

JSON内で使用する公開画像は、Contentドメインから参照しても解決できるよう `https://machiverse.app/...` の絶対URLを使用します。

`root/` は公開物のみを置くディレクトリです。内部資料や未公開データは配置しないでください。

## GitHub Pages

`.github/workflows/pages.yml` が `main` への更新を検知し、`root/` だけをGitHub Pagesの成果物としてデプロイします。

初回のみ、GitHubのリポジトリ設定で次を設定します。

1. `Settings` → `Pages` → `Build and deployment` のSourceを **GitHub Actions** にする。
2. Custom domainへ `content.machiverse.app` を設定する。
3. DNSで `content.machiverse.app` のCNAMEを `machiverse-project.github.io` へ向ける。
4. 証明書の発行後、HTTPSを有効にする。

公開成果物にも `root/CNAME` を含めています。
