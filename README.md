# MachiVerse Content

MachiVerse公式Webサイトなどから参照する、公開コンテンツ配信用リポジトリです。

## 公開ディレクトリ

GitHub Pagesでは、リポジトリ直下の `root/` を公開ルートとして配信します。

- `root/feeds/mio-devlog.json` — MIO DEVLOG / 南雲の開発日記
- `root/feeds/world-feed.json` — 公式インスタンス向け WORLD FEED

公開URL:

- `https://content.machiverse.app/feeds/mio-devlog.json`
- `https://content.machiverse.app/feeds/world-feed.json`

## 更新方針

投稿データの通常更新は `root/feeds/` 配下のJSONだけを編集します。Webサイト側の表示ロジック・CSSは `MachiVerse-Website` で管理します。

`root/` は公開物のみを置くディレクトリです。内部資料や未公開データは配置しないでください。
