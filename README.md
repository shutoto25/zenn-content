# Zenn Content 📝

Zenn記事とブック管理用リポジトリです。GitHub連携によりコンテンツを管理します。

## 🚀 セットアップ

### 1. リポジトリをクローン
```bash
git clone https://github.com/shutoto25/zenn-content.git
cd zenn-content
```

### 2. 依存関係をインストール
```bash
npm install
```

### 3. Zenn CLIでプレビュー
```bash
npm run preview
```

## 📖 使用方法

### 新しい記事を作成
```bash
npm run new:article
```

### 新しいブックを作成
```bash
npm run new:book
```

### ローカルでプレビュー
```bash
npm run preview
```
ブラウザで `http://localhost:8000` を開いてプレビューできます。

## 📁 ディレクトリ構造

```
.
├── articles/          # 記事ファイル（.md）
├── books/            # ブックディレクトリ
├── package.json      # プロジェクト設定
└── README.md         # このファイル
```

## ✍️ 記事の書き方

### フロントマター例
```yaml
---
title: "記事のタイトル"
emoji: "😎"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["javascript", "react"]
published: false
---
```

### ファイル名のルール
- 12〜50文字の半角英数字、ハイフン、アンダースコア
- 例: `my-first-article.md`

## 🔗 リンク

- [Zenn](https://zenn.dev/)
- [Zenn CLI](https://zenn.dev/zenn/articles/zenn-cli-guide)
- [GitHub連携について](https://zenn.dev/zenn/articles/connect-to-github)

---

Happy Writing! ✨