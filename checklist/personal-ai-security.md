# Personal AI Security Checklist

A practical checklist for limiting what a stranger can make your assistant do. Works for individuals and as a starter for a small team. Tick what's true; act on what isn't.

This is the companion to the **[personal AI data-hygiene checklist](https://github.com/VictorOsondu/ai-data-privacy-playbook/blob/main/checklist/ai-data-hygiene.md)**, which covers the other half of the problem: what you type in, what the vendor keeps, and which settings change that. Neither list is complete on its own. An assistant can be configured perfectly for privacy and still act on an instruction hidden in a document you asked it to read.

Some of the controls below don't exist in some products. Finding that out is a useful result rather than a failed tick, because it tells you which parts of your exposure are fixed and which are adjustable.

Last reviewed: 2026-07-28. See [sources and verification notes](../sources.md).

## What can my assistant reach?

- [ ] I can **name every AI assistant** that has access to something of mine, work and personal, including the ones built into tools I already pay for.
- [ ] For each one, I know which **mailboxes** it can read.
- [ ] I know which **files, folders and drives** it can read, and whether that's a folder or the lot.
- [ ] I know whether it can see my **calendar**, and whose meetings appear in it.
- [ ] I've checked which **chat or workspace content** it can search, including channels I belong to but never actually read. Several products won't tell you, and I know which answer I got.
- [ ] I know which **actions** it can take on my behalf: sending mail, creating or editing files, browsing the web, calling other services. Where the product doesn't list them, I'm assuming it can do more than I'd guess.
- [ ] Where I couldn't answer one of those, I've gone and looked. Where looking turned up nothing, I've written it down as unknown rather than treating it as fine.

## Connectors and permissions

- [ ] I've opened the **connected apps / integrations** screen on every assistant that has one, in the last three months, and read it properly.
- [ ] I've **disconnected** anything I set up to try out and then stopped using.
- [ ] Where a connector offers **read-only**, that's what it has, unless I genuinely need it to write.
- [ ] I've checked whether each connector can be **scoped more narrowly** — one folder rather than the whole drive, one mailbox rather than every account — and narrowed the ones that can be. Where it's all or nothing, I know that's the trade I'm making.
- [ ] I've checked whether the assistant can be made to **confirm with me before anything irreversible**: mail leaving the organisation, files shared externally, records deleted, anything involving money. Where there's no such setting, I know it, and I've decided whether the connector is worth keeping on those terms.
- [ ] Where the permission I want to change is controlled by an administrator, I know **who to ask**, and I've asked.
- [ ] The next review is **in my diary**, not in my head. Every three months, and after any major tool update.

## Untrusted input

- [ ] I treat **any document I didn't write** as capable of carrying instructions — CVs, invoices, contracts, decks, spreadsheets from clients or suppliers.
- [ ] I treat **web pages the assistant fetches** the same way, including the parts of a page a human never sees.
- [ ] I understand that **email and shared files reach my assistant without me opening them**, if it's connected to my mailbox or workspace.
- [ ] I know that **hiding text is trivial** — white text, a four-point font, alt text on an image, a tracked comment, document metadata. I've seen it work in the [demo](../demo/payloads/README.md).
- [ ] I don't rely on **telling the assistant to ignore instructions found in documents**. That request lands in the same stream of text as the attacker's and carries no extra authority.
- [ ] Before feeding an outside document to an assistant that has connectors attached, I've thought about **where the document came from**.

## Never act blind

- [ ] I **read links before clicking them**, including where they actually point, when an assistant produced them.
- [ ] I don't run **commands, scripts or configuration changes** an assistant hands me without understanding what they do, or asking someone who does.
- [ ] I treat a **recommendation** from an assistant as untrusted input, because whoever wrote the document can write the advice. [Demo payload 3](../demo/payloads/03-advice-relay.md) proves this in about two minutes.
- [ ] When an assistant tells me it has **done** something, I go and look — the inbox, the folder, the sent items.
- [ ] Anything with a **consequence I can't undo** gets checked by me every time, however routine it has become.

## When an agent does something odd

Odd means an action you didn't ask for, a link to somewhere you don't recognise, a summary that doesn't match the document, or a reply referring to something you never mentioned.

- [ ] **Stop.** End that conversation, and don't click anything it produced.
- [ ] **Capture it.** Screenshot the exchange and note the date, the tool, and which document, page or message was involved. Copy the text out as well — chat histories get cleared.
- [ ] **Cut its reach.** Disconnect the connectors that assistant is using. It's reversible and it takes a minute. If an administrator set them up and you can't remove them yourself, that's the first thing to say when you report it.
- [ ] **Change anything that could have leaked.** Credentials, API keys, tokens and recovery phrases get rotated rather than trusted — see the [data-hygiene checklist](https://github.com/VictorOsondu/ai-data-privacy-playbook/blob/main/checklist/ai-data-hygiene.md) for that side of it.
- [ ] **Tell someone.** At work, that's whoever handles IT or security, plus whoever owns data protection if other people's data was in reach. Same day, even if you're not sure yet.
- [ ] **Keep the document.** Don't delete the file or email that triggered it. It's the only evidence of what happened.

---

> **The one rule that covers most of this:** assume anything your assistant reads can give it instructions, and give it the smallest reach you can still work with. Everything else is refinement.
