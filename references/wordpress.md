# WordPress implementation guidance

## PHP translation functions

Use the project's correct text domain and WordPress gettext APIs, including `__()`, `_e()`, `_x()`, `_ex()`, `_n()`, and `_nx()` as appropriate. Prefer escaped output variants such as `esc_html__()`, `esc_attr__()`, `esc_html_x()`, or escaping at the correct output boundary. Escaping depends on output context; do not mechanically replace all calls with one escaping function.

Use literal source strings and literal text domains where required for extraction. Follow current WordPress coding standards and project conventions.

## Translator comments

Use comments beginning `translators:` immediately before the relevant translation call when placeholders, abbreviations, or unexpected meaning require explanation. A translator comment adds guidance without creating a new gettext key. Do not use a distinct `_x()` context merely to document a placeholder.

## Variables and formatting

Keep complete message templates translatable. Prefer numbered `sprintf()` placeholders when translators may need to reorder variables. Do not interpolate variables into the original string before translation. Escape dynamic values and output according to context. When placeholders contain markup or HTML, evaluate safety and translator flexibility carefully.

## JavaScript

For JavaScript, use the WordPress `@wordpress/i18n` APIs and ensure the script's translation catalog is correctly registered and loaded. Inspect the build pipeline and text domain. Avoid assuming PHP-only translation checks cover JS.

## Locale-sensitive UI

Check date/time, numbers, currency, names, text direction, and accessible labels. Use WordPress locale-aware formatting functions where suitable rather than manually imposing English formats. Test RTL layout where relevant. Do not confuse translated strings with full locale-aware behavior.

## Verification

Where available, use WordPress coding standards / i18n linting, string extraction, tests, and targeted searches. Automated checks find API misuse but cannot reliably judge grammatical flexibility. Inspect actual rendered messages and callers. Do not claim a successful extraction or test unless performed.

## Compatibility and catalog maintenance

Preserve public functions, hooks, filters, and stable identifiers. Refactoring a string assembly helper may require examining all callers and downstream extensions. Note changed `msgid`/`msgctxt` pairs and likely translation-review workload. Do not promise that fuzzy matching will recover every previous translation.
