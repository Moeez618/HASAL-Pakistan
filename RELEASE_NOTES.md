# Release Notes

## 2026-06-04

### Added

- Blog posts セクションに `Enable mobile slider` 設定を追加し、モバイル画面で記事一覧を横スクロールスライダー表示に切り替え可能にしました。

### Verification

- `shopify theme check`: passed with no offenses.
- `sections/section-blog.liquid` schema JSON parsing passed.

## 2026-05-19

### Added

- カートページセクションに `Show quantity selector` 設定を追加し、Quantity selector の表示 / 非表示をテーマエディタから切り替え可能にしました。
- カートページセクションに `Show subtotal note` 設定を追加し、「配送料、税金、割引コードはチェックアウト時に計算されます」の表示 / 非表示を切り替え可能にしました。

### Fixed

- カートページの Quantity selector と削除リンクの重なりを解消し、Drawer と同じく数量操作と削除導線が縦に整理されるよう調整しました。
- Quantity selector の横幅と入力欄の左右余白を拡張し、数量値と増減アイコンが重ならないようにしました。
- カート Ajax の割引コード更新、数量更新、削除処理で失敗時にボタンや入力欄が無効のまま残らないよう復帰処理を追加しました。
- Cart refresh / Cart drawer event listener の解除漏れを修正し、Theme editor や section 再読み込み時の重複リスナー発生を防止しました。
- カート内 upsell / bundle 商品の重複判定を部分一致から区切り付きの完全一致に変更し、商品IDやhandleの一部一致で誤除外されるリスクを解消しました。

### Verification

- `node --check assets/theme.dev.js`: passed.
- `node --check assets/theme.js`: passed.
- `sections/cart.liquid` schema JSON parsing passed.
- `git diff --check`: passed.

## 2026-05-11

### Added

- Broadcast の Release Notes ページに Cream by Solstar の全リリースノートを掲載しました。
- Cream の `Version 3.0.1` から `Version 3.4.9` までの更新内容を日本語で確認できるようにしました。
- Release Notes ページ専用の CSS スコープを追加し、背景色、文字色、罫線、余白、フォントサイズが Broadcast テーマの CSS 変数に追従するようにしました。
- Cream manual ページの Custom code セクションに Cream の `manual.md` 全内容を掲載しました。
- Cream manual ページにカテゴリタブと機能別の「詳細を見る」展開 UI を追加しました。

### Fixed

- Resolved all standard Shopify Theme Check errors.
- Added the missing `countdown-timer` theme block used by slideshow image and video blocks.
- Removed missing product 3D model asset references for `component-model-viewer-ui.css` and `product-model.js`.
- Updated Japanese locale keys to match the default English locale structure.
- Fixed missing translation references for product tabs, cart discount removal, quantity labels, inventory labels, pricing labels, and video accessibility labels.
- Replaced the unsupported `product_option_value` filter usage with the current product option value object.
- Added missing `width` and `height` attributes to image output paths flagged by Theme Check.
- Removed duplicate render arguments in header localization and tab collection image rendering.
- Updated gift card font preloading to use Shopify's `preload_tag` filter.
- Resolved all standard Shopify Theme Check warnings by removing unused Liquid assignments, normalizing variable names, initializing captured output buffers, and limiting suppressions to dynamic Liquid markup false positives.
- Cream manual ページの Custom code を 50KB 未満に圧縮し、Shopify の `Liquid file size cannot exceed 50 kilobytes` エラーを回避しました。
- Cream manual ページ内の重複 `h1` を削除し、ページ本体の見出し構造と競合しないようにしました。
- Cream manual の「概要」項目を bullet から外し、機能名に添える説明文として表示するようにしました。
- Cream manual のタブと「詳細を見る」に、Header メニューリンクと同じ下線ホバーアニメーションを適用しました。

### Performance

- Added `fetchpriority="high"` to the first template hero image path so the mobile LCP poster image is prioritized.
- Prioritized the first image block in early Rich text sections to address the desktop LCP image that PageSpeed reported as lazy-loaded.
- Removed unnecessary high-priority image hints from lazy-loaded mobile menu images.
- Removed preload/high-priority hints from the loading-screen image and added explicit image height output to reduce layout and resource-priority noise.
- Ensured the shared image snippet always passes an explicit empty `alt` value when image alt text is blank.
- Added a loading-screen enable setting that defaults off so the decorative loader does not block LCP rendering unless explicitly enabled.
- Added explicit height and fallback empty alt output to hero images, including video posters.
- Added a high priority hint to the first video poster image path and ensured generated video fallback images include empty alt text.
- Added more responsive image candidates around common mobile and desktop render widths to reduce oversized image downloads.
- Changed `swatches.css` to preload and apply asynchronously to reduce render-blocking CSS.

### Verification

- `shopify theme check --no-color`: passed with no offenses.
- `git diff --check`: passed.
- Locale JSON parsing passed for `locales/ja.json` and `locales/en.default.json`.

### Remaining Notes

- Strict `theme-check:all` still reports asset size findings for large CSS/JavaScript files. These are performance refactor candidates and should be handled separately from this bug-fix pass.
