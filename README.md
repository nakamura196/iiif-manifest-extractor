# IIIF Manifest 抽出ツール

IIIF Manifestから各巻（range/structure）の **label** と **最初のCanvas URL** を抽出するWebツールです。

## 機能

- IIIF Manifest URLを入力すると、`structures` に含まれる各rangeの情報を抽出
- 各巻のlabelと最初のCanvas URLを一覧表示
- 抽出データをJSONでコピー・ダウンロード可能

## 使い方

1. [ツールを開く](https://toyo-bunko.github.io/iiif-manifest-extractor/)
2. Manifest URLを入力
3. 「抽出」ボタンをクリック
4. 各巻のlabelと最初のCanvas URLが表示される

## 用途

- リンクをクリックしたときに該当仏典の冒頭ページを開くためのデータ抽出
- IIIF Manifestの構造解析

## サンプル

増上寺蔵高麗版大蔵経:
```
https://jodoshuzensho.jp/zojoji/koryo/manifests/001/001/0001/koryo_001_001_0001.json
```

## 技術仕様

- 純粋なHTML/CSS/JavaScriptで構成（サーバー不要）
- IIIF Presentation API 2.0/3.0 対応
- GitHub Pagesでホスティング可能

## ライセンス

MIT License
