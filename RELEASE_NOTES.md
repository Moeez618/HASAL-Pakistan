# Release Notes

## 2026-05-11

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
