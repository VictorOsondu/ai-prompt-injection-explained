# Annotated cases

Three walkthroughs of prompt injection in systems people actually used. Each one takes a documented case and goes through it slowly: what the attacker's text did, what the system did with it, why that worked, and what would have made the damage smaller.

One of these happened to a real business, in public. Two were researcher demonstrations that got reported to the vendor and fixed, where nobody was harmed. Each file says which it is in its opening lines. That distinction does real work, because most of what's written about prompt injection is careful disclosure work, and reading it as a casualty list gets the risk badly wrong in both directions.

## The cases

| Case | Class | The thing it teaches |
| --- | --- | --- |
| [Chevrolet of Watsonville](chevrolet-watsonville-dollar-chatbot.md) | Happened, December 2023 | A system prompt isn't a security boundary |
| [Slack AI](slack-ai-private-channel-exfiltration.md) | Researcher demonstration, August 2024 | An assistant reading across trust boundaries erases them |
| [EchoLeak](echoleak-m365-copilot.md) | Researcher demonstration, June 2025 | Careful behaviour isn't a control |

Read Chevrolet first. It's the simplest, and the mechanism underneath it is the same one the other two rely on.

## Where the sourcing lives

This repository doesn't restate sourcing. Every factual claim in these walkthroughs links to the matching entry in the **[AI Incident Library](https://github.com/VictorOsondu/ai-incident-library)**, which carries the primary references, the confidence notes, and an explicit list of what not to infer from each case.

That's deliberate. Two copies of a source table drift apart, and the one people quote is usually the stale one. If a claim here matters to you, follow the link and read the entry it came from.

The same rule governs detail. Where a library entry records a mechanism only coarsely — as it does for EchoLeak, because the researchers' own writeup went offline — the walkthrough stays coarse too. Plausible-sounding specifics that nobody established are worse than an admitted gap.

## Two cases that aren't here

The incident library also holds two AI-related compromises from 2025 that people sometimes file alongside these:

- **[Amazon Q Developer extension, July 2025](https://github.com/VictorOsondu/ai-incident-library/blob/main/incidents/2025-07-amazon-q-developer-extension-compromise.md)** — a threat actor committed malicious code into the repository behind an AI coding extension, and it shipped to the marketplace in a released version.
- **[Nx "s1ngularity", August 2025](https://github.com/VictorOsondu/ai-incident-library/blob/main/incidents/2025-08-nx-s1ngularity-supply-chain.md)** — a stolen publishing token let an attacker push malicious releases of a widely used build tool, whose install script hunted the filesystem for credentials and enlisted local AI command-line tools to help.

Both are worth reading. Neither belongs here, because neither turns on an assistant reading text and mistaking it for an instruction. In both cases, hostile code arrived through a software distribution channel that everyone downstream trusted, and it ran as code. That's a supply-chain problem with AI tooling in the blast radius. Nx gets closest to our subject, since the payload used AI tools as part of the theft, and it's still the attacker's own code doing the work rather than the attacker's words steering somebody else's assistant.

Different failure mode, different controls. Mixing the two makes both harder to think about.

---

Back to [the explainer](../README.md), or work through the [checklist](../checklist/personal-ai-security.md).
