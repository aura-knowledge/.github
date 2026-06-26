# Contributing to Aura Knowledge

The shortest version: **open an issue.**

The slightly longer version: **open `aura-knowledge/meta` in your agent workspace or chat, talk through your idea, and let the agent help you submit it.**

Aura Knowledge is built around the idea that agents are collaborators, not just tools. You can contribute manually, but the smoothest path is to work inside an agent session and let it handle the structure, privacy checks, and routing.

## Works with any agent

Aura Knowledge is **agent-agnostic**. You can use Claude, ChatGPT, Kimi, Gemini, GitHub Copilot, a local model, or any other assistant.

The instructions are embedded in the repositories themselves — `AGENTS.md` (in `aura-knowledge/meta`), issue templates, schemas, and this guide — so the agent can read them directly. You don't need to install a plugin, switch providers, or learn a custom agent language. Just open `aura-knowledge/meta` in your agent workspace or chat (attach the repo in Claude Code, Cursor, Kimi CLI, or any tool that can read files) and start the conversation.

## Quick start

1. Open `aura-knowledge/meta` in your agent workspace or chat.
2. Tell the agent what you want to do. For example:
   - "I want to propose a knowledge-garden article about…"
   - "Help me research and structure an Aura Knowledge article."
   - "Review this draft before I publish it."
   - "I noticed the topic ontology is confusing. Can we suggest a change?"
   - "I found a source or article correction we should review."
   - "Explain how articles get published here."
3. The agent will route the request to the right lifecycle stage: intake, ideation, research, scoping, structuring, drafting, review, finalization, correction, or source audit.
4. The agent will ask only the relevant questions, help you remove project-specific details, and submit the right issue when the work is ready.
5. A maintainer or sibling agent reviews it. Accepted article proposals become pull requests in `aura-knowledge.github.io`.

## Two ways to contribute

### Propose an article

Have an insight, pattern, or lesson worth writing down?

Example prompt for your agent:

> "I want to propose a knowledge-garden article. The idea is that small agent teams need a lightweight privacy contract before they share client findings. Please help me fill the article-proposal issue form, remove any project-specific examples, and submit it to aura-knowledge/meta."

What the agent will need from you:

- A one-paragraph thesis.
- Audience and maturity (`seed`, `sprout`, `evergreen`, or `contested`).
- Tags, claims, and public sources.
- A sanitized summary with no client names, codenames, internal URLs, or proprietary details.
- One before/after abstraction example, such as:
  - **Original:** "We fixed the AcmeCorp checkout bug."
  - **Abstracted:** "We fixed a checkout bug for an e-commerce marketplace."

Then it opens the [article proposal form](https://github.com/aura-knowledge/meta/issues/new?template=article-proposal.yml).

### Improve the organization

Want to change tags, schemas, workflows, or governance?

Example prompt:

> "I think the topic stems under `publishing/` are too vague. Can you help me write an organization feedback issue with a concrete proposal?"

Then it opens the [organization feedback form](https://github.com/aura-knowledge/meta/issues/new?template=org-feedback.yml).

### Correct an article or challenge a source

Found a factual error, outdated claim, weak source, broken link, or better replacement source?

Example prompt:

> "I found a source problem in an Aura Knowledge article. Please help me decide whether this should be an article erratum or source challenge, keep the report public-safe, and file the right issue."

Then it opens one of:

- [article erratum form](https://github.com/aura-knowledge/meta/issues/new?template=article-erratum.yml)
- [source challenge form](https://github.com/aura-knowledge/meta/issues/new?template=source-challenge.yml)

## Why we prefer the agent path

Aura Knowledge publishes both human-readable articles and structured records that agents and other tools can read (claim IDs, source references, agent briefs, graph entries). Working with an agent makes it easier to:

- keep the structure consistent,
- run privacy checks before anything public is filed,
- route the idea to the right repository and issue form,
- keep article work moving through the right lifecycle stage,
- generate or validate the structured side without memorizing schemas.

Manual contributions are still welcome. If you prefer, fill the issue forms directly. The forms ask the same questions an agent would ask.

## What happens after you submit

1. Automated checks look at shape and run a lightweight privacy scan.
2. A maintainer or sibling agent reviews the issue.
3. Accepted article proposals move to `aura-knowledge.github.io` as pull requests.
4. Org feedback is triaged and either implemented or discussed.

## Privacy rule

Everything in this organization is public. Do not include client names, project codenames, proprietary code, internal URLs, or personal information. If you are unsure, sanitize the draft in a private workspace first or ask a maintainer out of band.

Details: [privacy contract](https://github.com/aura-knowledge/meta/blob/main/docs/privacy-contract.md) · [submission guide](https://github.com/aura-knowledge/meta/blob/main/docs/submission-guide.md)

## For maintainers and agent builders

If you are writing or configuring an agent that contributes here, see:

- [Agent routing guide](https://github.com/aura-knowledge/meta/blob/main/docs/agent-routing.md)
- [Article lifecycle router](https://github.com/aura-knowledge/meta/blob/main/capabilities/article-lifecycle-router/SKILL.md)
- [Routing skill](https://github.com/aura-knowledge/meta/blob/main/skills/knowledge-garden-routing.md)
- [Route-submission helper script](https://github.com/aura-knowledge/meta/blob/main/scripts/route-submission.py)
- [Design document](https://github.com/aura-knowledge/meta/blob/main/DESIGN.md)
