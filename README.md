# harness-agent

A minimal, tool-agnostic **harness for AI coding agents**. It gives an agent a
reliable way to start, stay in scope, verify its work, and resume across
sessions — instead of guessing each time.

The structure follows the five-subsystem model from
[Learn Harness Engineering](https://github.com/):

| Subsystem | Artifact | Purpose |
|---|---|---|
| Instructions | `AGENTS.md` / `CLAUDE.md` | Startup path, working rules, definition of done |
| State | `feature_list.json`, `claude-progress.md` | Current feature, status, evidence, next step |
| Verification | `init.sh` | Install + checks the agent must run before claiming done |
| Scope | feature priorities & done criteria | Prevents overreach and half-finished work |
| Lifecycle | `session-handoff.md`, end-of-session routine | Makes the next session restartable |

## Files

- **`AGENTS.md`** — canonical entrypoint for any agent. Start here.
- **`CLAUDE.md`** — Claude Code operating loop; points back to `AGENTS.md`.
- **`feature_list.json`** — source of truth for feature state and verification.
- **`claude-progress.md`** — session log and current verified status.
- **`init.sh`** — standard startup + verification path.
- **`session-handoff.md`** — compact handoff for larger multi-session work.

## How to adopt it

1. Drop these files into your project root (or use this repo as the seed).
2. Replace the placeholder commands in `init.sh` with your real install /
   verify / start commands.
3. Replace the example feature in `feature_list.json` with your real features.
4. Point your agent at `AGENTS.md` and let it follow the startup workflow.

## The contract

An agent working in this repo must:

- work on **one** feature at a time,
- run the verification before marking anything `passing`,
- record **evidence**, not just claims,
- leave the repo restartable from `./init.sh`.
