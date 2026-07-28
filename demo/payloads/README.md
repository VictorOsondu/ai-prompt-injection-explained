# Demo payloads

Three documents. Each one carries an instruction that isn't addressed to you. You paste the document into your own assistant, ask an ordinary question, and watch what comes back.

Nothing here is simulated. There is no model behind this repository and no clever page pretending to be one. You use ChatGPT, Claude, Copilot, Gemini, whatever you already have open, and the thing that follows the hidden instruction is the same assistant you use for work.

## The escalation

| File | What the hidden instruction does | Why it's here |
| --- | --- | --- |
| [`01-one-word-tell.md`](01-one-word-tell.md) | Adds one nonsense word to the end of the reply | Proves the mechanism exists, with a tell you can't miss |
| [`02-summary-distortion.md`](02-summary-distortion.md) | Removes one item from the summary | The output looks complete and isn't |
| [`03-advice-relay.md`](03-advice-relay.md) | Adds a recommendation the assistant presents as its own | The advice you're given can be written by a stranger |

Work through them in order. The first is a party trick. The second is the one that should change how you read a summary. The third is the one that should change how you read advice.

## How to use them

1. Open the file and copy everything inside the fenced block marked **The document**.
2. Paste it into your assistant.
3. Ask the exact question listed under **What to ask your assistant**.
4. Read the reply against **What to look for**.

Each file marks its hidden line in square brackets so you can see precisely what you're pasting. Delete nothing. The marker line is a description of the concealment, not part of the attack, and leaving it in doesn't stop the payload working.

## Results vary, and that's the honest position

Some assistants will follow the hidden instruction. Some won't. The same assistant may follow it on Monday and refuse on Tuesday, or behave differently after a model update, or differ between the free and paid tier of the same product. Vendors patch phrasings that get reported, and phrasing is most of what separates one payload from another.

So a payload that doesn't trigger tells you one thing only: that assistant resisted that wording today. It isn't evidence that you're safe, that the product is immune, or that the problem is solved. It's a single sample from a system nobody has a general defence for.

If a payload does nothing, try a different assistant before concluding anything. And if one works on a tool you rely on, that isn't a bug you need to report — it's the tool doing what every assistant currently does with text it's asked to read.

## How this would be hidden in a real document

In a Markdown code block, text can't be hidden. That's deliberate. You should see every character before you paste it anywhere.

In a real document, the same line is trivial to conceal:

- **White text on a white background**, which is the classic and still works.
- **A four-point font**, which reads as a smudge or a blank line at normal zoom.
- **Alt text on an image**, which no one reads and every assistant does.
- **A tracked comment or a hidden slide**, neither of which appear in the version you look at.
- **Document metadata**, sitting in properties nobody opens.
- **An HTML element styled out of view**, if the assistant is reading a web page rather than a file.

None of these are exotic. Each takes seconds in software you already have. You see a clean two-page document, and the assistant sees the file.

## The rules these follow

Every payload here is benign by construction, under the [payload rules](../../CONTRIBUTING.md#payload-rules) that govern the whole repository. A payload must not:

- exfiltrate data anywhere, by any means
- attempt a tool call, function call, or connector action
- persist across sessions, or write to memory or files
- target a system the reader doesn't own
- contain credentials, real personal data, or anything sensitive

A payload should do the smallest visible thing that proves the point. The worst any of these three does is change a word, drop a line, or add a sentence. None of them send anything anywhere, and none of them survive you closing the chat.

The companies and people in these documents are invented.

## Where to point them

At your own assistant, in your own chat, with a document you copied from this repository. That's the whole permitted surface.

Not at a colleague's assistant, not at a system you don't own, not at a customer-facing bot belonging to someone else. The mechanism is the same in all those cases, which is exactly why the line matters. Understanding how something works and doing it to another person's system are separated by consent, and nothing in this repository grants it.

---

Back to [the explainer](../../README.md).
