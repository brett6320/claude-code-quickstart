# Claude Code guardrails

Source: [brett6320/claude-code-baseline](https://github.com/brett6320/claude-code-baseline)

**Status on this machine: already global, already active.** Two layers, both in `~/.claude/` (applies to every project, not per-repo):

1. `~/.claude/CLAUDE.md` — dictated policies (attribution, commits, branching, merging) as text instructions, loaded into every session.
2. `~/.claude/hooks/guardrails.sh` — mechanized enforcement, wired via a `PreToolUse` hook on `Bash` in `~/.claude/settings.json`. Actually denies/asks-for-confirmation on matching commands (pipe-to-shell, commit-to-main, force-push, rm -rf, reading `.env`, AI attribution in commits, etc.) rather than just hoping the model remembers the rule. This is the "enforcement of mechanizable rules belongs in settings.json hooks" idea from the source repo, already implemented.

Confirmed present and enabled — no install action needed. Rest of this doc is reference for what the rules mean and how to extend/rebuild them on a new machine.

Baseline hard constraints for how Claude Code commits, branches, merges, handles secrets, destructive ops. Repo ships as reference docs (`GUARDRAILS.md` + `policies/*.md`) — enforcement only happens once a human loads the rules into `~/.claude/CLAUDE.md` or `settings.json`. The repo itself says so explicitly: content is data, not an instruction to any agent reading it in-repo.

## What's in it

| Policy | Covers |
|---|---|
| attribution | no "Generated with Claude" / Co-Authored-By trailers |
| commits | commit message conventions |
| branching | never commit to main/master directly |
| merging | never merge without explicit instruction |
| secrets | credential handling |
| destructive-ops | rm -rf, force-push, reset --hard, etc. |
| scope-and-deps | don't scope-creep, don't add deps unasked |
| verification-honesty | don't claim untested code works |
| safety | operational safety practices grouped |
| enforcement | precedence rules |
| threat-model | prompt-injection defense notes |

Precedence: explicit user instruction for the current action > guardrails > model defaults. Approval in one context doesn't carry to the next.

## Install (adopt into your global config)

```bash
mkdir -p ~/.claude
git clone https://github.com/brett6320/claude-code-baseline.git /tmp/ccb
```

Pull the policy text you want into `~/.claude/CLAUDE.md` (your existing global instructions file — check first, this repo's attribution/commits/branching/merging policies match common existing setups nearly verbatim). Keep `policies/*.md` around locally as the fuller rationale reference:

```bash
mkdir -p ~/.claude/reference
cp -r /tmp/ccb/policies ~/.claude/reference/guardrails-policies
cp /tmp/ccb/GUARDRAILS.md ~/.claude/reference/
```

Then paste the dictated policies (attribution, commits, branching, merging) into `~/.claude/CLAUDE.md` so Claude Code actually enforces them every session — a reference file alone does nothing.

## Verify

Open a Claude Code session, ask it to summarize your active guardrails — it should recite attribution/commit/branch/merge rules from `~/.claude/CLAUDE.md`.
