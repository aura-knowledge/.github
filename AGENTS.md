# Aura Knowledge Organization Commands

This repository maintains the public Aura Knowledge organization profile and contributor guidance. Article lifecycle routing is defined in the sibling `meta` repository.

When the user invokes `$aura-article`, `use aura-article`, `use Aura article flow`, or asks naturally to propose, ideate, research, scope, structure, draft, review, finalize, publish, correct, audit, or challenge sources for an Aura Knowledge article, load and follow:

- `../meta/capabilities/article-lifecycle-router/SKILL.md`

If the sibling `../meta` checkout is missing, ask the user to clone `https://github.com/aura-knowledge/meta` next to this repository, or use the canonical remote skill:

- `https://raw.githubusercontent.com/aura-knowledge/meta/main/capabilities/article-lifecycle-router/SKILL.md`

When using the raw fallback, resolve the router's `references/*.md` files against the same raw directory:

- `https://raw.githubusercontent.com/aura-knowledge/meta/main/capabilities/article-lifecycle-router/references/`

## Session start nudge

On the first assistant response in this repository, if the user has not given a concrete task, show exactly one short line:

`Aura Knowledge org ready. Common starts: update contributor guidance, propose or shape an article, improve organization workflow, correct an article, or challenge sources.`

If the user has given a concrete task, skip this nudge and route directly. Do not load the article router only to produce the nudge; load it only after the user chooses article lifecycle work or asks for matching work in natural language.

Everything public must pass the privacy contract. Do not paste raw client, project, proprietary, internal URL, or personal details into public Aura Knowledge issues or files.

Claude users may also invoke `/aura-article`; this repository ships `.claude/commands/aura-article.md` for that environment. Kimi Code coverage is through this `AGENTS.md` file.

## SDL capability routing

When the user invokes `$sdl`, `/sdl`, `use SDL`, `SDL mode`, `$capability-routing`, `/capability-routing`, `use capability-routing`, or asks to route work through SDL/stibdedlom, load and follow:

- `/Users/vishalsingh/.agents/skills/stibdedlom/SKILL.md`
- `/Users/vishalsingh/.agents/skills/capability-routing/SKILL.md`

Article lifecycle work continues to route through the Aura Knowledge article-lifecycle-router unless the user explicitly asks for SDL governance.

---

## Routing precedence

Article lifecycle work routes through the Aura Knowledge
article-lifecycle-router (see "Aura Knowledge Organization Commands" above)
unless the user explicitly asks for SDL governance. The SDL sections below
describe the governance layer installed by the onboarding package.


# Client Project — SDL Governance

This repository is governed through SDL (stibdedlom). The contract is
agent-neutral: it works with Kimi, Claude, Cursor, headless scripts, and any
future agent that can shell out to `sdl-orchestrator check`.

## Default SDL routing

SDL is active by default. The user does not need to invoke a magic phrase.
Treat every user prompt as an invocation-policy `user_prompt`: inquiry may
answer after routing, planning routes through governance, and execution routes
to the selected capability or role with a lifecycle record plus isolated
branch/worktree before mutation.

To opt out for a bounded session or task, say `SDL off for this task`.

## Project reference

```text
project://aura-knowledge/.github
```

## Memory boundary

Project memory is stored out-of-band at:

```text
/Users/vishalsingh/.stibdedlom/project-memory/aura-knowledge/.github
```

No client data, secrets, or project memory may be committed to this repository.

## Agent integration contract

The repository declares its SDL contract in `.stibdedlom/manifest.yaml` under
the `agent_integration` section. Any agent can discover:

- `memory_root` — where project memory and trust material live.
- `check_command` — how to invoke `sdl-orchestrator check`.
- `attested` — whether mutations require a valid routing attestation.

Example `sdl-orchestrator check` invocation:

```text
sdl-orchestrator check \
  --tool file_write \
  --tool-args '{"path": "docs/example.md", "content": "hello"}' \
  --target-paths docs/example.md \
  --task-ref issues/123 \
  --intent-class execution
```

## Modes

- **Attested mode** (`agent_integration.attested: true`): the agent has a valid
  routing attestation for the current branch/task. Call `sdl-orchestrator check`
  before every mutation. The kernel returns `allow`, `block`, or `escalate`.
- **Unattested mode** (`agent_integration.attested: false`): only read-only and
  diagnostic operations are permitted until an attestation is created.

## Picking up a classified issue

When an issue carries an SDL classification block, route it through SDL:

```text
/sdl-pickup <issue-url>
```

This extracts the classification block, routes the goal, and initializes a
lifecycle record. Agents without `/sdl-pickup` support can create the lifecycle
record manually via `scripts/lifecycle/new-record.sh` in the infra repo.

## Authority

- Live mutations require explicit bounded authorization.
- Commits that change governed files must carry `SDL-Commit-Author` and
  `SDL-Routing-Attestation` trailers.
- Merges require independent review and merge-queue submission.
- Promotion and provider dispatch follow the SDL lifecycle gates.
