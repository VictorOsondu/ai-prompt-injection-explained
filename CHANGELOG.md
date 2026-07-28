# Changelog

This project follows [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added
- Repository scaffolded to Playbook Standard v1: licence, contribution and conduct rules, security note, Markdown lint profile, content-check workflow, issue templates, and the directory skeleton for the demo, examples, and checklist.
- **[CONTRIBUTING.md](CONTRIBUTING.md)** — payload rules governing every demo payload in this repository.
- **[sources.md](sources.md)** — header and verification conventions, no entries yet.
- **[README.md](README.md)** — the main explainer: the one idea, why signature-based tooling misses it, the three routes text arrives by, what changed once assistants could act, and an honest account of what reduces exposure.
- **[demo/index.html](demo/index.html)** — a static demo page presenting each payload as three steps with a copy button. No build step, no framework, and no external requests of any kind, so it works with the connection off.
- **[demo/payloads/](demo/payloads/)** — three benign payloads, escalating from a one-word tell to an omitted summary item to a relayed recommendation, each with the question to ask and the tell to look for.

### Notes
- `practitioner-built`. Annotated examples and the checklist land in later commits, so the README links to them ahead of their arrival.
- Demo payloads are run against the reader's own assistant. Nothing in this repository simulates a model, and results vary between assistants, attempts, and model versions.
