# books

Zennのブックファイルを格納するディレクトリです。

## ディレクトリ構造
各ブックは専用のディレクトリを持ち、その中にconfig.yamlと複数のMarkdownファイルを配置します。

```
books/
└── book-slug/
    ├── config.yaml
    ├── chapter1.md
    ├── chapter2.md
    └── ...
```

## ブックの作成
```bash
npm run new:book
```
