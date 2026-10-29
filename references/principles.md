# Linguistic principles for i18n

## Translate meaningful units, not English fragments

Allow translators to reorder words, alter inflection, choose articles and prepositions, and restructure punctuation. Do not concatenate separately translated articles, adjectives, verbs, or sentence halves to manufacture user-visible sentences. Trace the entire assembled message. A placeholder for dynamic data is often appropriate; placeholders do not automatically make arbitrary grammar composable.

Avoid imposing English word order on other languages. Swedish adjective agreement, German case and word order, Russian inflection and plural patterns, and other language-specific constructions can expose flaws invisible in English.

## Gettext keys and context

Within a text domain, the gettext lookup key is the original source string (`msgid`) plus optional context (`msgctxt`). Identical source strings with identical context share one translation; the runtime cannot choose different translations for different uses of the same key.

Short strings deserve special scrutiny: `Filter`, `Group`, `Duplicate`, and `Refund` can be nouns, verbs, imperatives, or adjectives depending on UI usage. Check the actual interface and other occurrences before deciding.

Use `_x()` and related functions when *distinct translations* may be required. Keep contexts as short as possible while still useful: `noun`, `verb`, `status` may suffice, but use a short semantic distinction when grammatical category alone is insufficient. Reuse context consistently for the same meaning.

Use a `translators:` comment to explain an otherwise opaque string or placeholder when a distinct lookup key is **not** required. Do not substitute context for comments: gratuitous contexts inflate catalogs, duplicate work, and reduce translation reuse.

Changing a source string or context changes its gettext key. Catalog-update tools may propose fuzzy matches from older entries; translators must review and approve them, and fuzzy entries are generally not included in compiled catalogs. Matching behavior depends on the tool and is not guaranteed. Avoid churn and flag key changes in reports.

## Plurals and counts

Never assume a singular/plural distinction based solely on English rules. Use WordPress plural APIs where appropriate and supply actual counts. Avoid constructing plural messages by attaching suffixes or concatenating fragments. Consider zero and languages with multiple plural categories. Do not assert that a particular language has a specific number of plural forms without verifying.

## Names, articles, and grammatical cases

Country names, currencies, roles, and other variable nouns may change form according to the surrounding sentence. An English-specific list of country names requiring `the` is not a locale-independent solution. Do not assume that translating `the` (or making it empty) repairs the phrase. Prefer whole-message translation and, where needed, locale-aware name forms or a different message design. Ask the developer when intended combinations are unclear.

## Preserve translator choice

Prefer simple, complete messages. Placeholders should be numbered when reordering is plausible. Avoid embedding markup in translatable strings when a safe structure is possible, but preserve necessary translator control of placement. Provide clear translator comments for non-obvious placeholders. Do not over-fragment catalogs for theoretical ambiguities that do not exist in the actual UI.
