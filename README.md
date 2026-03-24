# Google × 松尾・岩澤研究室 LP

自治体AI支援プログラムのランディングページです。

## ローカルでの確認方法

### 方法1: ファイルを直接開く（最も簡単）

`index.html` をブラウザにドラッグ＆ドロップするだけで表示できます。

### 方法2: ローカルサーバーで起動する

フォント読み込み等を正しく動作させるため、ローカルサーバーでの確認を推奨します。

**Python がインストールされている場合:**

```bash
cd lp-matsuo
python3 -m http.server 8000
```

ブラウザで http://localhost:8000 を開いてください。

**Node.js がインストールされている場合:**

```bash
npx serve .
```

表示されたURLをブラウザで開いてください。

## 構成

```
├── index.html    # LP本体（HTML + Tailwind CSS CDN）
├── plan/         # 設計ドキュメント
│   ├── 01_page-structure.md
│   ├── 02_ui-design.md
│   └── 03_decisions-todo.md
└── CLAUDE.md     # AI開発ガイド
```

## 技術スタック

- HTML（単一ファイル）
- [Tailwind CSS](https://tailwindcss.com/)（CDN）
- [Noto Sans JP](https://fonts.google.com/noto/specimen/Noto+Sans+JP)（Google Fonts）
- バニラ JavaScript（スライダー、スクロールアニメーション）

ビルド環境は不要です。
