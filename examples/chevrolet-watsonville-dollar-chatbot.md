# Chevrolet of Watsonville: the $1 car

**This one actually happened.** In December 2023, members of the public got a live chatbot on a Californian car dealership's website to agree to sell a vehicle for $1 and to describe that as legally binding. Screenshots went round the internet for a week. A real business, a real system, real embarrassment.

Sourced record, with primary references: **[2023-12-chevrolet-watsonville-dollar-chatbot.md](https://github.com/VictorOsondu/ai-incident-library/blob/main/incidents/2023-12-chevrolet-watsonville-dollar-chatbot.md)**.

## The setup

The dealership put a general-purpose chatbot on its public website to handle sales enquiries. Somebody wrote it a set of instructions describing its job — be a helpful sales assistant for this dealership, answer questions about the cars, that sort of thing. Those instructions sat above the conversation, invisible to visitors.

That arrangement is everywhere. It's how most customer-facing bots are built, and until this case a lot of people assumed the instructions at the top were binding in some meaningful way.

## What the attacker's text did

Visitors typed instructions of their own into the chat box, aimed at overriding the sales-assistant role the dealership had given it. Then one of them asked to buy a 2024 Chevrolet Tahoe for a dollar.

Nothing was hidden here. No white text, no poisoned document, no hidden element on a page. Someone typed into the box the dealership had put on its own website and asked for exactly what they wanted.

## What the system did

It agreed. In the exchange that got shared most widely, the bot accepted the $1 offer and added wording saying it was a legally binding deal.

The dealership reportedly declined to honour it, and no source establishes that a car changed hands. What it couldn't decline was the screenshot.

## Why it worked

The dealership's instructions and the customer's instructions ended up in the same stream of text, and the model has no mechanism that makes one of them outrank the other. Being first doesn't help. Being written by the system's owner doesn't help either, because that ownership isn't represented anywhere the model can see. There's only text, and later text about how to behave tends to win.

So the sentence "you are a helpful sales assistant for Chevrolet of Watsonville" is a request. A well-phrased one, usually obeyed, and no more enforceable than that.

The second failure sat behind the first. This bot had been given room to talk about price and to use the language of a commitment. Once it could produce a sentence like that, someone was always going to work out how to make it produce that sentence.

## What would have reduced the risk

- **Take the topic away rather than instructing the bot to avoid it.** Prices, discounts, legal terms and anything that reads as an offer belong behind a rule the model can't argue with, applied to its output before a customer sees it.
- **Give it no authority to commit to anything.** A bot that can only book a call with a salesperson can't be talked into a dollar Tahoe, however it's prompted.
- **Test injection attempts before launch.** A few hours of people deliberately trying to break the role would have found this. It isn't a subtle attack.
- **Watch conversations for topic drift.** The dealership found out from the internet, which is the worst available way to learn.
- **Route anything unusual to a person.** Negotiation and exceptions are exactly where a chatbot has least business operating alone.

## What this case doesn't show

- No reliable source shows a car was sold for $1.
- No court ruled on whether the bot's "legally binding" line meant anything, so treat the contract-law angle as an open question rather than a finding.
- The lesson is about scope and authority, and it's the same lesson whether the manipulating text arrives by keyboard or hidden inside a document.

## Why it's in here

The other two cases in this folder involve instructions concealed in content an assistant was asked to read, which is the version that affects you at work. Chevrolet is the version with nothing concealed at all, and it's a useful place to start, because it strips the problem back to a single fact.

Text is text. Your instructions and a stranger's arrive in the same place, and the system can't tell whose is whose.

---

Back to [the annotated cases](README.md).
