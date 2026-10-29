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

## Background and original resources

This skill builds on Tor-Björn Fjellner's work explaining common linguistic pitfalls in WordPress internationalization:

- [Hints about i18n — let your code shine all over the world](https://gsm.fjellner.com/hints-about-i18n-let-your-code-to-shine-all-over-the-world/) — the underlying article.
- [Enable truly global use of your code — avoid the typical i18n pitfalls](https://wordpress.tv/2023/10/01/enable-truly-global-use-of-your-code-avoid-the-typical-i18n-pitfalls/) — presentation recording, WordCamp Europe 2023, Athens.
- [Presentation slides](https://gsm.fjellner.com/2023/06/10/slides-from-presentation-about-i18n-in-athens-on-june-10-2023/) — slides from the Athens talk.

## Status

Initial working draft. Examples are illustrative; verify against current WordPress APIs and project-specific requirements. Contributions and test cases are welcome.

## Feedback and contributions

Feedback is very welcome, especially questions, real-world examples of translation difficulties, and suggestions for improving the guidance.

- Use [Discussions](https://github.com/tobifjellner/wordpress-i18n-helper-skill/discussions) to ask questions, share useful examples, or explore ideas.
- Open an [Issue](https://github.com/tobifjellner/wordpress-i18n-helper-skill/issues) to report a problem, identify missing guidance, or suggest a specific improvement.
- WordPress developers are also encouraged to join the [global WordPress contributor Slack](https://make.wordpress.org/chat/) and reach out in the [#polyglots channel](https://wordpress.slack.com/archives/C02RP50LK) to discuss translation and internationalization questions with the community.

When sharing examples, include enough context to explain the linguistic problem and, where possible, what a translator would need to express. Contributions to the repository are also welcome.

## License

GPL-2.0-or-later. See [LICENSE](LICENSE).
