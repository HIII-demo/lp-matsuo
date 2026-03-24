# UI設計方針 v2 — 「信頼感 × モダン」

## コンセプト

松尾研究所のブランド（ダーク×シアン）を土台に、
**Glassmorphism Hero + Bento Grid + グラデーションアクセント**で2025年感を出す。
自治体担当者が見ても安心、テック関係者が見てもイケてる、のバランス。

---

## 1. 松尾研究所サイトからの継承要素

| 要素 | 抽出値 | LP での扱い |
|------|--------|-------------|
| メインカラー | #000000, #313131 | → ダークネイビー #0F172A に昇華（真っ黒より品がある） |
| アクセント | #0693e3（シアン） | → そのまま継承 + グリーン #34d399 へのグラデ追加 |
| ボタン | pill型 (rounded-full) | → 継承。CTAはグラデーション化 |
| スタイル | ミニマル + モダン企業 | → ミニマルベースにGlassmorphism/Bento要素を加える |
| 印象 | 先端技術 × 社会実装 | → Heroのパーティクル演出で「先端感」を視覚化 |

---

## 2. スタイルミックス

```
ベース:          Minimalism & Swiss Style（グリッド、余白、高コントラスト）
Hero:           Glassmorphism（frosted glass カード + ダーク背景 + 動き）
訴求セクション:   Bento Grid（Apple風、非対称カード、rounded-2xl）
アクセシビリティ:  Accessible & Ethical（WCAG AA準拠、全体を通して）
```

---

## 3. カラーシステム

### カラートークン
```
Primary:        #0F172A   (ダークネイビー)
Secondary:      #1E293B   (ミッドネイビー)
Accent:         #0693e3   (シアンブルー ← 松尾研継承)
Accent Green:   #34d399   (エメラルドグリーン ← Google感を加味)
Background:     #F8FAFC   (オフホワイト)
Card:           #FFFFFF   (ホワイト)
Text:           #0F172A   (ダークネイビー)
Text Muted:     #64748B   (スレートグレー)
Border:         #E2E8F0   (ライトボーダー)
Section Alt BG: #F1F5F9   (セクション交互背景)
Ring/Focus:     #0693e3   (アクセントと同色)
```

### グラデーション（差別化の鍵）
```
Hero背景:       linear-gradient(135deg, #0F172A 0%, #1a2744 50%, #0F172A 100%)
Hero光彩:       radial-gradient(ellipse at 30% 50%, rgba(6,147,227,0.2), transparent 60%),
                radial-gradient(ellipse at 70% 50%, rgba(52,211,153,0.12), transparent 60%)
CTAボタン:      linear-gradient(135deg, #0693e3, #34d399)
セクション境界:   1px solid + linear-gradient(to right, transparent, #0693e3, #34d399, transparent)
Bento強調カード: 背景に淡いグラデ border（1px gradient border trick）
```

---

## 4. タイポグラフィ

### フォント構成
```
見出し（日本語）:  Noto Sans JP  700   ← クリーンでモダン。Serif は外す
見出し（英字）:    Inter         700   letter-spacing: -0.02em ← テック感
本文:             Noto Sans JP  400
ラベル/小見出し:   Inter         500   uppercase + tracking-wider（英字時）
数値/データ:      Inter         600   tabular-nums
```

```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Noto+Sans+JP:wght@300;400;500;700&display=swap');
```

### タイプスケール
```
h1:     48px / weight 700 / line-height 1.2 / tracking -0.02em  (Hero用、インパクト)
h2:     36px / weight 700 / line-height 1.3 / tracking -0.01em  (セクション見出し)
h3:     24px / weight 700 / line-height 1.4                      (サブ見出し)
h4:     20px / weight 500 / line-height 1.5                      (カード見出し)
body:   16px / weight 400 / line-height 1.75                     (本文)
small:  14px / weight 400 / line-height 1.6                      (補足)
label:  12px / weight 500 / line-height 1.5 / uppercase tracking-wider (ラベル)
```

---

## 5. セクション別デザイン

### S1. Hero — Glassmorphism + パーティクル
```
┌──────────────────────────────────────────────────┐
│  [ダークネイビー背景 #0F172A]                        │
│  [CSSパーティクル or メッシュグラデーションの微細な動き]  │
│  [シアン/グリーンの光彩がゆっくり漂う]                  │
│                                                    │
│  ┌─── Glassmorphism Card ───────────────────┐     │
│  │  backdrop-filter: blur(16px)              │     │
│  │  bg: rgba(255,255,255,0.08)               │     │
│  │  border: 1px solid rgba(255,255,255,0.15) │     │
│  │  rounded-2xl                              │     │
│  │                                           │     │
│  │  [小見出し] Google × 松尾・岩澤研究室       │     │
│  │  [h1] AIで、地域の未来を                    │     │
│  │       切り拓く。                           │     │
│  │  [本文] 日本の自治体・地方のための...         │     │
│  │  [CTA] グラデーションpillボタン              │     │
│  └──────────────────────────────────────────┘     │
│                                                    │
│  ↓ スクロールインジケーター                         │
└──────────────────────────────────────────────────┘
```

### S2. 取組概要 — クリーンセクション
```
白背景、max-w-4xl中央寄せ
左にテキスト、右にパートナーロゴ（Google + 東大松尾研）
「営利ではなく社会課題の解決」をキーメッセージとして大きく
下部にグラデーション境界線
```

### S3. 訴求ポイント — Bento Grid（最重要セクション）
```
┌──────────────────────────────────────────┐
│  Section Alt BG (#F1F5F9)                │
│                                          │
│  ┌──────────────┐  ┌──────────────┐     │
│  │              │  │              │     │
│  │  2x2 大カード │  │  1x2 カード   │     │
│  │  最先端AI技術  │  │  自治体特化   │     │
│  │  アイコン+     │  │              │     │
│  │  説明文       │  ├──────────────┤     │
│  │              │  │  1x1 カード   │     │
│  │              │  │  実証→実装    │     │
│  └──────────────┘  └──────────────┘     │
│                                          │
│  カード: rounded-2xl (16px)               │
│  ホバー: scale(1.02) + shadow-lg          │
│  強調カード: gradient border               │
└──────────────────────────────────────────┘
```

### S4. 事例一覧 — カードグリッド
```
白背景、3カラムグリッド
各カード: 上部に自治体イメージ(仮)、下部にテキスト
ホバー: translateY(-4px) + shadow-lg
タグ: 「防災」「教育」等の小さなpill型バッジ
```

### S5. 導入の流れ — タイムライン
```
縦ラインにステップを配置
ライン色: グラデーション（シアン→グリーン）
各ステップ: 丸ナンバー + テキスト + 期間目安
無料/有料の切り替え点にグラデーションバッジ
  「ここまで無料」← 明確に
```

### S6. トレーニング — ダークセクション
```
ダークネイビー背景（Hero呼応）+ 白テキスト
Glassmorphismカード2-3枚横並び
  - AIコネクトアカデミー
  - サイバーセキュリティ
  - 人材育成ワークショップ
背景にうっすらグラデーション光彩
```

### S7. 動画 — フルワイド
```
Section Alt BG
max-w-4xl で YouTube 埋め込み
rounded-2xl + shadow-xl
上下に余白たっぷり
```

### S8. CTA — ダーク + グラデーション
```
ダークネイビー背景（Heroと呼応、ページを閉じる感覚）
中央にキャッチコピー + 大きなグラデーションCTAボタン
ボタン: linear-gradient(135deg, #0693e3, #34d399) + hover glow
```

### S9. フッター
```
#0F172A 背景、白テキスト
ロゴ + リンク + コピーライト
シンプルに
```

---

## 6. コンポーネントスタイル

### ボタン
```
プライマリCTA:
  background: linear-gradient(135deg, #0693e3, #34d399)
  color: white
  rounded-full (pill型)
  px-8 py-3.5
  shadow: 0 4px 14px rgba(6,147,227,0.3)
  hover: shadow-lg + brightness(1.1) + translateY(-1px)
  transition: all 200ms ease

セカンダリ:
  bg transparent
  border: 1.5px solid #0F172A
  color: #0F172A
  rounded-full
  hover: bg #0F172A, color white

ゴースト:
  bg transparent
  color: #0693e3
  hover: underline
```

### カード（通常）
```
bg: white
border: 1px solid #E2E8F0
rounded-2xl (16px)
shadow: 0 1px 3px rgba(0,0,0,0.05)
padding: 24-32px
hover: shadow-lg + translateY(-2px) + scale(1.01)
transition: all 250ms ease
```

### カード（Bento 強調）
```
position: relative
overflow: hidden
before疑似要素でgradient border:
  border: 1px solid transparent
  background-clip: padding-box
  外周: linear-gradient(135deg, #0693e3, #34d399) を border に
rounded-2xl (16px)
```

### カード（Glassmorphism — ダークセクション用）
```
bg: rgba(255, 255, 255, 0.06)
backdrop-filter: blur(16px)
-webkit-backdrop-filter: blur(16px)
border: 1px solid rgba(255, 255, 255, 0.1)
rounded-2xl (16px)
color: white
```

### バッジ/タグ
```
bg: #E0F2FE（シアン薄）or #D1FAE5（グリーン薄）
color: #0369A1 or #065F46
rounded-full
px-3 py-1
text-xs font-medium
```

### セクション間隔
```
セクション間:  py-24 (96px) ～ py-32 (128px)
内部余白:     gap-8 (32px)
コンテナ:     max-w-6xl (1152px), mx-auto, px-6
セクション見出し: mb-16 (64px) 中央寄せ
```

---

## 7. アニメーション

### Hero
```
パーティクル/メッシュ:
  CSSグラデーションの位置を @keyframes で 20s ease infinite ループ
  background-size: 200% 200%
  → JSなしで軽量な動き

Glassmorphismカード:
  ページロード時 opacity 0 → 1, translateY(30px → 0)
  600ms ease-out, delay 300ms
```

### スクロールトリガー（IntersectionObserver）
```
フェードイン:     opacity 0→1, translateY(24px→0), 500ms ease-out
スタガー:        子要素ごとに +80ms ディレイ
Bento カード:    scale(0.96→1) + opacity, 400ms
数値カウントアップ: 事例セクションの成果数値（requestAnimationFrame）
タイムライン:     ライン伸長アニメーション（height 0→100%）
```

### ホバー
```
カード:   translateY(-2px) + shadow-lg, 200ms ease
ボタン:   brightness(1.1) + translateY(-1px), 200ms ease
リンク:   color transition, 150ms
```

### prefers-reduced-motion
```
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
→ すべてのアニメを無効化。コンテンツは初期状態で表示。
```

---

## 8. 技術スタック

**単一HTML + Tailwind CSS v3 CDN**

```html
<!-- Tailwind -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- フォント -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Noto+Sans+JP:wght@300;400;500;700&display=swap" rel="stylesheet">

<!-- アイコン: Lucide (CDN) -->
<script src="https://unpkg.com/lucide@latest"></script>
```

Tailwind カスタム設定:
```javascript
tailwind.config = {
  theme: {
    extend: {
      colors: {
        primary: '#0F172A',
        secondary: '#1E293B',
        accent: '#0693e3',
        'accent-green': '#34d399',
      },
      fontFamily: {
        sans: ['Inter', 'Noto Sans JP', 'sans-serif'],
      },
      borderRadius: {
        '2xl': '16px',
        '3xl': '24px',
      }
    }
  }
}
```

---

## 9. レスポンシブ

```
Mobile:   ~767px    1カラム、Bento→縦積み、Hero文字小さめ(36px)
Tablet:   768-1023  2カラム、Bento 2x2→2カラム化
Desktop:  1024-1439 3カラム、フルレイアウト
Wide:     1440+     max-w-6xl で中央固定
```

---

## 10. アクセシビリティ（WCAG AA準拠）

- [ ] テキストコントラスト比 4.5:1 以上
- [ ] 大テキスト（18px+太字 or 24px+）は 3:1 以上
- [ ] タッチターゲット 44x44px 以上
- [ ] フォーカスリング 3px, accent色
- [ ] ARIA ラベル（アイコンボタン等）
- [ ] スキップリンク
- [ ] セマンティックHTML（h1→h2→h3 階層厳守）
- [ ] prefers-reduced-motion 完全対応
- [ ] cursor-pointer on clickable
- [ ] SVGアイコン（Lucide）、絵文字不使用
- [ ] alt テキスト（仮画像にも設定）
- [ ] フォームlabel紐付け

---

## 11. デザインサマリー

```
松尾研ブランド（ダーク × シアン × ミニマル）
  ×
モダンUI（Glassmorphism × Bento Grid × グラデーション）
  ×
自治体向け信頼（WCAG AA × 高コントラスト × セマンティック）
  ＝
┌────────────────────────────────────────┐
│  ダークHero + パーティクル光彩 +          │
│  Glassmorphismカードで先端感              │
│           ↓                             │
│  白ベースのクリーン本体                   │
│  Bento Gridで訴求ポイント                │
│  グラデーション(シアン→グリーン)がアクセント │
│           ↓                             │
│  ダークCTAで閉じる（Hero呼応）             │
│                                         │
│  全体を通してInter + Noto Sans JPの       │
│  クリーンタイポグラフィ                    │
│  ピル型ボタン + グラデーションCTA           │
│  控えめだが効果的なスクロールアニメーション   │
└────────────────────────────────────────┘
```
