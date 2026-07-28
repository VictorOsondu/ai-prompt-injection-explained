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
- **[examples/](examples/)** — annotated walkthroughs of three documented cases: Chevrolet of Watsonville, Slack AI, and EchoLeak. Each covers what the attacker's text did, what the system did, why it worked, and what would have reduced the risk.

### Notes
- `practitioner-built`. The checklist lands in a later commit, so the README links to it ahead of its arrival.
- The annotated cases don't restate sourcing. Every factual claim links to the matching [AI Incident Library](https://github.com/VictorOsondu/ai-incident-library) entry, which carries the primary references. Each file states in its opening lines whether the case happened or was a researcher demonstration. The two 2025 supply-chain compromises in the library are named in `examples/README.md` and deliberately excluded, being a different failure mode.
- Demo payloads are run against the reader's own assistant. Nothing in this repository simulates a model, and results vary between assistants, attempts, and model versions.
