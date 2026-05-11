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

### Verification

- `shopify theme check --output json --no-color`: passed with `errors=0`.
- `git diff --check`: passed.
- Locale JSON parsing passed for `locales/ja.json` and `locales/en.default.json`.

### Remaining Notes

- Standard Theme Check still reports warnings only, mainly from dynamic Liquid structure:
  `UnclosedHTMLElement`, `UndefinedObject`, `UnusedAssign`, and `VariableName`.
- Strict `theme-check:all` still reports asset size findings for large CSS/JavaScript files. These are performance refactor candidates and should be handled separately from this bug-fix pass.
