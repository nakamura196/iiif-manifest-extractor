# IIIF Manifest 抽出ツール

IIIF Manifestから各巻（range/structure）の **label** と **最初のCanvas URL** を抽出するWebツールです。

## 機能

- 複数のManifest URLを一括処理（1行に1つのURL）
- 各巻・各章のlabelと最初のCanvas URLを一覧表示
- CSV/JSON形式でのエクスポート
- 処理進捗のリアルタイム表示

## 使い方

1. [ツールを開く](https://nakamura196.github.io/iiif-manifest-extractor/)
2. Manifest URLをテキストエリアに入力（複数行可）
3. 「抽出」ボタンをクリック
4. 各巻のlabelと最初のCanvas URLが表示される
5. 必要に応じてCSV/JSONでダウンロード

## 用途

- 各巻・各章の冒頭ページへのリンク作成
- IIIF Manifestの構造解析

## サンプル

国立国会図書館デジタルコレクション「校異源氏物語」（複数URL一括処理の例）:
```
https://dl.ndl.go.jp/api/iiif/3437686/manifest.json
https://dl.ndl.go.jp/api/iiif/3437687/manifest.json
```

## 制限事項

- **IIIF Presentation API v2のみ対応**: v3形式のManifest（`items`を使用するもの）には対応していません
- **CORS制限**: Manifestを提供するサーバーがCORSを許可している必要があります

## 技術仕様

- 純粋なHTML/CSS/JavaScriptで構成（サーバー不要）
- GitHub Pagesでホスティング

## 貢献

貢献に興味がある方は [CONTRIBUTING.md](CONTRIBUTING.md) をご覧ください。

## ライセンス

[MIT License](LICENSE)
