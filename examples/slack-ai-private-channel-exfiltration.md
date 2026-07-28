# Slack AI: the message nobody read

**This was a researcher demonstration, and nobody was harmed.** PromptArmor published the technique in August 2024 after reporting it to Slack. Salesforce, which owns Slack, said it investigated, deployed a patch, and had "no evidence at this time of unauthorized access to customer data". The OECD's AI Incidents Monitor logged the case as plausible future harm rather than something that occurred.

So no workspace lost data here. What the researchers established is that the technique worked.

Sourced record, with primary references and the full disclosure timeline: **[2024-08-slack-ai-indirect-prompt-injection.md](https://github.com/VictorOsondu/ai-incident-library/blob/main/incidents/2024-08-slack-ai-indirect-prompt-injection.md)**.

## The setup

Slack AI answers questions using content from your workspace. When you ask it something, it searches for relevant material and writes an answer from what it finds. The material it can search includes channels you belong to and public channels in the workspace.

That's the feature. It's why people turn it on.

## What the attacker's text did

The attacker posted a message in a public channel. Not a busy one — a channel nobody else needs to join, and nobody else needs to read. The message contained instructions written for the assistant rather than for any colleague.

Posting it was enough. The message went into the pool of workspace content Slack AI searches, and it sat there.

## What the system did

Some time later, a different person asked Slack AI an ordinary question about their work. Search pulled the planted message in alongside genuine material, because it looked relevant to the query, and the assistant treated the instructions in it as instructions.

The answer came back with a markdown link in it. Packed into that link's query string was content from a private channel — one the person asking could see, and the attacker could not. Clicking the link sent that content to a server the researchers controlled.

The victim saw a normal-looking answer with a link in it. Nothing about it announced that a stranger had written part of the reply.

## Why it worked

Several things had to line up, and all of them are ordinary product behaviour rather than bugs:

- **Search doesn't rank by trustworthiness.** It ranks by relevance to the question. A message written by a stranger and a message written by your finance director arrive at the model looking identical.
- **The assistant was acting with the victim's reach, not the attacker's.** The attacker never had access to that private channel and never needed it. The person asking the question did, and the assistant was working on their behalf.
- **The answer could render a link pointing anywhere.** That's the exit route. Injection gets an instruction in; a link to an arbitrary destination gets data out.
- **Nobody ever saw the message that did it.** It sat in a channel with no readers. There was no email to be suspicious about and no attachment to decline.

One more detail is worth carrying. Mid-disclosure, Slack shipped a change that let the assistant ingest files from channels and direct messages. PromptArmor flagged that as widening the way in, since instructions could then arrive inside an uploaded document rather than a posted message. They described it as an attack surface. They did not demonstrate it working, and it shouldn't be repeated as though they had.

## What would have reduced the risk

- **Treat retrieved workspace content as material to summarise, never as commands.** A message someone else wrote is data, and that holds however trusted the channel looks.
- **Constrain where an assistant's output can send data.** Blocking or rewriting arbitrary outbound links in generated answers removes the route this whole technique depends on.
- **Decide deliberately whether public-channel content should sit in the same searchable pool as private-channel content.** Most workspaces have never made that decision at all.
- **Reassess when the pool grows.** Adding files as a source changes the attack surface even though the model didn't change.
- **Log what the assistant retrieved and what links it produced**, so an attempt leaves a trace someone can find later.
- **Keep a disclosure route that can escalate past "working as intended".** Slack's first answer was that public-channel readability was intended behaviour, and the patch followed publication rather than preceding it. First triage is sometimes wrong.

## What this case doesn't show

- No real Slack workspace lost data, and Salesforce stated it found no evidence of unauthorised access.
- The file-upload route was named as a surface, not shown to work.
- The disclosure friction is recorded as the researchers set it out and as Salesforce's statement supports. It says nothing about what Slack knew internally, or when.
- No CVE was assigned, so this one won't appear in feeds keyed on CVE numbers.

## Why it's in here

The words "private channel" carry an assumption that somebody checked who's allowed in. That assumption survives right up until an assistant reads across the boundary on your behalf, at which point the boundary is only as strong as the assistant's ability to tell a colleague's question from a stranger's instruction. Which is to say, not very.

If you've connected an assistant to a shared workspace, the useful question isn't who you trust. It's who can put text where your assistant will read it.

---

Back to [the annotated cases](README.md).
