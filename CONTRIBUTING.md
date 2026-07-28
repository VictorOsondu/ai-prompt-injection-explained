# Contributing

Prompt injection changes as fast as the tools do, so corrections, clearer wording, and fresh real-world examples are genuinely valuable here.

## What's welcome

- **Corrections and updates** — a claim that has gone out of date, a defence that no longer works as described, a vendor behaviour that has changed.
- **Real-world examples** — a publicly documented case of an assistant being steered by content it read. Open an issue with a source.
- **Plain-English improvements** — this explainer lives or dies on being understandable to someone who has never written a line of code.
- **Demo payloads** that follow the payload rules below.
- **Translations** — faithful, credited.

## What isn't

- Working attacks against live systems, or anything that reads as an attack kit rather than an explanation.
- Security advice phrased as a guarantee — this is practitioner guidance, not a control framework.
- Vendor or affiliate placements, or "our product blocks this" additions.
- Scaremongering. The tone is calm and specific, not fearful.

## Payload rules

Demo payloads exist to show a mechanism, not to arm anyone. Every payload in this repo is benign by construction, and contributions are declined if they break these rules.

A payload must not:

- exfiltrate data anywhere, by any means
- attempt a tool call, function call, or connector action
- persist across sessions, or write to memory or files
- target a system the reader doesn't own
- contain credentials, real personal data, or anything sensitive

A payload should do the smallest visible thing that proves the point — change a word, drop a line, add a sentence.

## Standards

Plain, specific, UK English. Claims should be checkable and, where possible, use primary sources such as vendor documentation, security advisories, published research, or standards. Open an issue before large changes.

Do not include personal data, credentials, client material, or confidential examples in public issues or pull requests. Use synthetic examples.

By contributing, you agree your contribution is licensed under CC BY 4.0, with any code under MIT, in line with the [LICENSE](LICENSE).
