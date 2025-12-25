# IIIF Manifestから各巻の冒頭ページを抽出するツールを作成しました

## はじめに

IIIF（International Image Interoperability Framework）を利用したデジタルアーカイブでは、複数巻や複数章で構成される資料を1つのManifestにまとめることがあります。このような場合、各巻・各章の冒頭ページへのリンクを作成したいというニーズがあります。

今回、IIIF Manifestから各巻（range/structure）の**label**と**最初のCanvas URL**を抽出するシンプルなWebツールを作成しました。

**ツールURL**: https://nakamura196.github.io/iiif-manifest-extractor/

**GitHub**: https://github.com/nakamura196/iiif-manifest-extractor

## 機能

- 複数のManifest URLを一括処理（1行に1つのURL）
- 各巻・各章のlabelと最初のCanvas URLを一覧表示
- CSV/JSON形式でのエクスポート
- 処理進捗のリアルタイム表示

## 使い方

1. ツールを開く
2. Manifest URLをテキストエリアに入力（複数行可）
3. 「抽出」ボタンをクリック
4. 結果が表形式で表示される
5. 必要に応じてCSV/JSONでダウンロード

## サンプル

以下のManifest URLで動作を確認できます。

**国立国会図書館デジタルコレクション「校異源氏物語. 巻一」:**
```
https://dl.ndl.go.jp/api/iiif/3437686/manifest.json
```

このManifestは源氏物語の各帖（きりつほ、ははきゝ、うつせみ、わかむらさき...など）がstructuresに定義されており、各帖の冒頭ページを抽出できます。

## 技術的な仕組み

### IIIF Presentation API v2のstructures

IIIF Presentation API v2では、`structures`プロパティを使って論理的な構造（目次）を定義できます。

```json
{
  "structures": [
    {
      "@type": "sc:Range",
      "label": "目次",
      "ranges": ["range1", "range2", ...]
    },
    {
      "@id": "range1",
      "@type": "sc:Range",
      "label": "きりつほ",
      "canvases": [
        "https://example.com/canvas/p1",
        "https://example.com/canvas/p2",
        ...
      ]
    }
  ]
}
```

本ツールでは、`structures`内の各rangeから：
1. `label`（巻名・章名など）
2. `canvases`配列の最初の要素（冒頭ページのCanvas URL）

を抽出しています。

### フォールバック処理

`structures`が存在しない場合は、`sequences[0].canvases`の最初の要素を取得するフォールバック処理を実装しています。

## 制限事項

- **IIIF Presentation API v2のみ対応**: v3形式のManifest（`items`を使用するもの）には対応していません
- **CORS制限**: Manifestを提供するサーバーがCORSを許可している必要があります

## 実装

純粋なHTML/CSS/JavaScriptで構成されており、サーバーサイドの処理は不要です。GitHub Pagesで静的にホスティングしています。

主要な処理の流れ：

```javascript
// Manifestを取得
const response = await fetch(url);
const manifest = await response.json();

// structuresから各rangeを抽出
if (manifest.structures) {
  for (const structure of manifest.structures) {
    // 親range（rangesを持つもの）はスキップ
    if (structure.ranges && structure.ranges.length > 0) {
      continue;
    }
    // canvasesを持つrangeを処理
    if (structure.canvases && structure.canvases.length > 0) {
      const label = structure.label;
      const firstCanvas = structure.canvases[0];
      // 抽出データに追加
    }
  }
}
```

## おわりに

このツールは、デジタルアーカイブにおける資料へのリンク作成作業を効率化するために作成しました。シンプルな構成のため、必要に応じてカスタマイズも容易です。

ご質問やフィードバックがあれば、GitHubのIssueでお知らせください。

## 参考

- [IIIF Presentation API 2.1.1](https://iiif.io/api/presentation/2.1/)
- [IIIF Presentation API 3.0](https://iiif.io/api/presentation/3.0/)
- [国立国会図書館デジタルコレクション](https://dl.ndl.go.jp/)
