# MachiVerse Content

MachiVerse公式Webサイトなどから参照する、公開コンテンツ配信用リポジトリです。

## 公開ディレクトリ

GitHub Pagesでは、リポジトリ直下の `root/` を公開ルートとして配信します。

- `root/feeds/mio-devlog/config.json` — MIO DEVLOGの共通設定
- `root/feeds/mio-devlog/posts/YYYY-MM-DD.json` — MIO DEVLOGの日別投稿
- `root/feeds/world-feed.json` — 公式インスタンス向け WORLD FEED
- `root/index.json` — 公開フィードのマニフェスト

公開URL:

- `https://content.machiverse.app/feeds/mio-devlog/config.json`
- `https://content.machiverse.app/feeds/mio-devlog/posts/YYYY-MM-DD.json`
- `https://content.machiverse.app/feeds/world-feed.json`
- `https://content.machiverse.app/index.json`

## MIO DEVLOG

MIO DEVLOGの投稿は `Asia/Tokyo` を日付基準として、1日1JSONに分割します。

```text
root/feeds/mio-devlog/
├─ config.json
└─ posts/
   ├─ 2026-09-18.json
   ├─ 2026-09-17.json
   └─ ...
```

`config.json` にはプロフィールやセクション表示などの共通設定だけを置きます。

各 `posts/YYYY-MM-DD.json` は次の形で、そのJST日付の投稿だけを保持します。

```json
{
  "date": "2026-09-18",
  "posts": []
}
```

投稿がない日は日別JSONを作成する必要はありません。MachiVerse公式サイトは当日を含む直近7日分だけを取得し、存在しない日の404は投稿なしとして扱います。

## 更新方針

投稿データの通常更新は `root/feeds/` 配下のJSONだけを編集します。Webサイト側の表示ロジック・CSSは `MachiVerse-Website` で管理します。

MIO DEVLOGの通常更新では、該当するJST日付の `root/feeds/mio-devlog/posts/YYYY-MM-DD.json` だけを更新します。日付をまたいだら新しい日付ファイルを作成します。

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
