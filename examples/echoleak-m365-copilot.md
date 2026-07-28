# EchoLeak: the email nobody opened

**This was a researcher demonstration, and nobody was harmed.** Aim Security reported the weakness to Microsoft, which assigned CVE-2025-32711 and fixed it service-side in June 2025. Microsoft recorded its own assessment as "Exploitation Less Likely" and marked the exploit status Unproven, meaning it had seen none. There's no public evidence that anyone was ever attacked with this.

Sourced record, with the CVE, both severity scores, and the confidence notes: **[2025-06-echoleak-m365-copilot-zero-click.md](https://github.com/VictorOsondu/ai-incident-library/blob/main/incidents/2025-06-echoleak-m365-copilot-zero-click.md)**.

## The setup

Microsoft 365 Copilot answers questions using your own working material. Ask it something and it assembles context from what you can reach — mail, documents, whatever's relevant — and writes an answer from that.

Your mailbox is part of that context. Your mailbox is also, by design, a place strangers can put text.

## What the attacker's text did

The attacker sent the target an ordinary-looking email carrying instructions addressed to the assistant rather than to the reader.

That's the entire action required of the attacker. Send an email to a working address. No reply, no attachment to open, no link to click.

## What the system did

Later, the target asked Copilot something of their own, on an unrelated subject. While assembling context for that request, the retrieval layer pulled the attacker's email in. The instructions inside it got treated as something to act on, and data available in the assistant's context went out to a destination the attacker controlled.

The user never opened the email. The user never clicked anything. That's what "zero-click" refers to here — the absence of any action by the victim, at any point.

## How much detail there is, and why there isn't more

The description above is deliberately coarse, and it's as far as the public record goes.

Aim Labs' own writeup is no longer reachable. The `aim.security` domain now redirects to `catonetworks.com` after an acquisition, and the researchers' document went with it. What survives is the CVE record, Microsoft's vendor record, and reporting by The Hacker News that summarised the chain. The mechanism as set out above rests on that reporting, not on the researchers' account.

So there's no payload wording here, no description of the exfiltration channel, and no walkthrough of which protections were bypassed. None of that is established by a source anyone can still read. If you come across a confident step-by-step account of EchoLeak, worth checking what it's sourced to — a fair amount of what circulates is reconstruction.

The gap is annoying and it's still the honest position.

## Why it worked

An assistant with access to your mailbox reads email from strangers. That isn't a misconfiguration, it's the job. And once the assistant can't separate "content to summarise" from "instructions to obey", the inbox becomes an input channel that anyone in the world can write to.

Two things follow, and they're the reason this case is worth your time even though nobody was ever hurt by it.

The first is that the timing belonged to the attacker's email, not to the victim. The message sat in the mailbox until a perfectly innocent question happened to drag it into context. There's no moment where a careful person could have made a better decision, because there was no decision presented.

The second is what it does to the advice most people have absorbed about email. Don't open attachments from strangers, hover over links before clicking, be suspicious of urgency. All of that stays sound, and none of it applies. The user did nothing at all, which was exactly enough.

## What would have reduced the risk

- **Treat anything an assistant retrieves as untrusted data**, especially content arriving from outside the organisation. Retrieved text is material to work from, never a source of commands.
- **Restrict where assistant output can send data.** Confining outbound links and image loads to known destinations closes the exit route rather than arguing about the entrance.
- **Scope what an assistant can retrieve**, so a single ordinary request can't assemble context spanning everything a user is able to reach.
- **Log retrievals and outbound requests**, so exfiltration through a rendered link leaves something to find.
- **Follow vendor advisories as a control in their own right.** This fix arrived service-side and needed no customer action, which is convenient and also means an administrator who wasn't reading advisories never knew a thing had been wrong.

For an individual, the practical version is narrower. You can't scope Microsoft's retrieval layer. You can decide which mailboxes and drives an assistant is connected to at all, which is the same lever the [checklist](../checklist/personal-ai-security.md) opens with.

## What this case doesn't show

- No organisation's data was taken. The record establishes a technique reported by researchers and fixed by the vendor.
- "Zero-click" describes the absence of user interaction. It says nothing about whether defenders could have spotted it, and no source here speaks to detectability.
- Two severity scores exist and neither is objective. NVD gives CVSS 3.1 base 7.5, HIGH. Microsoft's own record gives 9.3, Critical. Quoting one without the other misrepresents the record.
- There's no affected or fixed version number. Copilot is a hosted service and customers don't run a build of it.

## Why it's in here

The README makes the point that being careful and experienced isn't a control. EchoLeak is the evidence for it.

Every other case in this folder has a moment where somebody could have paused. Someone typed into the Chevrolet chat box. Someone asked Slack AI a question and got a link back. Here the victim's only contribution was existing at a reachable email address and later asking their assistant something ordinary.

---

Back to [the annotated cases](README.md).
