# Contributing to IIIF Manifest Extractor

このプロジェクトへの貢献に興味を持っていただきありがとうございます。

## 貢献の方法

### Issue の報告

バグを発見した場合や機能リクエストがある場合は、[GitHub Issues](https://github.com/nakamura196/iiif-manifest-extractor/issues) で報告してください。

Issue を作成する際は、以下の情報を含めてください：

- 問題の詳細な説明
- 再現手順（バグの場合）
- 期待される動作と実際の動作
- 使用しているブラウザとバージョン
- 可能であれば、問題が発生した Manifest URL

### Pull Request

1. このリポジトリをフォークします
2. 新しいブランチを作成します (`git checkout -b feature/amazing-feature`)
3. 変更をコミットします (`git commit -m 'Add some amazing feature'`)
4. ブランチにプッシュします (`git push origin feature/amazing-feature`)
5. Pull Request を作成します

### コーディング規約

- インデントは2スペースを使用
- 日本語コメントは歓迎します
- 新機能を追加する場合は、README.md も更新してください

## 開発環境のセットアップ

このプロジェクトは純粋な HTML/CSS/JavaScript で構成されているため、特別なビルドツールは不要です。

1. リポジトリをクローン
   ```bash
   git clone https://github.com/nakamura196/iiif-manifest-extractor.git
   cd iiif-manifest-extractor
   ```

2. ローカルサーバーを起動（例：Python）
   ```bash
   cd docs
   python -m http.server 8000
   ```

3. ブラウザで `http://localhost:8000` を開く

## ライセンス

このプロジェクトに貢献することで、あなたの貢献が MIT License の下でライセンスされることに同意したものとみなされます。
