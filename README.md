# WordPress i18n Helper Skill

An open, reusable Agent Skill for reviewing and improving internationalization (i18n) in WordPress plugins and themes.

The goal is **translator-friendly code**, not simply passing mechanical gettext checks. The skill teaches developers *why* a construction can fail in other languages and helps AI coding assistants propose or implement safe corrections.

## Two modes

- **REVIEW (default):** Audit code, explain linguistic and technical problems, and recommend actionable improvements without editing files.
- **IMPROVE:** Apply developer-authorized corrections, ask when intent is unclear, preserve compatibility, and report validation and changed translation keys.

## Use

Install or reference this directory as an Agent Skill in a compatible coding assistant. Exact installation paths and invocation vary by environment. The entry point is [SKILL.md](SKILL.md); detailed material is in [references/](references/).

Example prompts:

> Review the internationalization of this WordPress plugin. Explain significant linguistic pitfalls with code locations and proposed corrections. Do not edit files.

> Improve i18n in these files. Fix unambiguous issues, but ask before changing product wording, behavior, or public APIs. Report translation-key changes.

## Principles

- Translate complete, meaningful units rather than English sentence fragments.
- Use gettext context only when identical source strings need different translations.
- Prefer translator comments for explanation, avoiding unnecessary catalog fragmentation.
- Review plurals, placeholders, grammatical agreement, and locale-sensitive formatting.
- Preserve developer intent and minimize unnecessary translation maintenance work.

## Status

Initial working draft. Examples are illustrative; verify against current WordPress APIs and project-specific requirements. Contributions and test cases are welcome.

## License

GPL-2.0-or-later. See [LICENSE](LICENSE).
