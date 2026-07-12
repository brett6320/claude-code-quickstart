# Claude Code guardrails

Only relevant if you use Claude Code (an AI coding assistant that runs in Terminal). Skip this if that's not you.

Source: [brett6320/claude-code-baseline](https://github.com/brett6320/claude-code-baseline)

## What this is, in plain terms

Claude Code can be told a standing set of rules it must always follow — e.g. "never commit code directly to the main branch," "never merge a pull request without being explicitly asked," "don't paste secret credentials into the terminal." This guide sets those rules up two ways:

1. **A text file** (`~/.claude/CLAUDE.md`) — instructions Claude Code reads and tries to follow.
2. **A script** (`~/.claude/hooks/guardrails.sh`) — an actual gatekeeper that inspects every command before Claude Code runs it, and blocks or asks for confirmation on risky ones (regardless of whether Claude "remembers" to follow the rule). This is the more reliable of the two.

## Where these files live

`~/.claude` is a hidden folder in your home folder (`~` means your home folder, e.g. `/Users/yourname`). "Hidden" means Finder doesn't show it by default. Two ways to get to it:

- **Via Finder:** open Finder → press `Cmd + Shift + G` → type `~/.claude` → Return.
- **Via Terminal**, to open the main rules file directly in TextEdit-like fashion:
  ```bash
  open -a TextEdit ~/.claude/CLAUDE.md
  ```
  (If the file or folder doesn't exist yet, create the folder first: `mkdir -p ~/.claude`, then create the file with the `open` command above.)

## What's in the guardrails repo

| Policy | Plain-English meaning |
|---|---|
| attribution | Don't credit "Claude" or "AI" in commits/PRs/docs |
| commits | Follow a consistent commit message style |
| branching | Never commit straight to the main/master branch — always use a separate branch |
| merging | Never merge a pull request unless explicitly told to, for that specific PR |
| secrets | Don't read or expose passwords/API keys/credential files |
| destructive-ops | Ask before anything hard to undo (force-delete, force-push, resetting history) |
| scope-and-deps | Don't add unrelated changes or new dependencies without being asked |
| verification-honesty | Don't claim code works without actually having tested it |
| safety | General operational safety practices |
| enforcement | Which rule wins if two rules conflict |
| threat-model | Defenses against malicious instructions hidden in files/websites |

**Rule of precedence:** what you explicitly ask for in the moment beats these guardrails, which beat Claude's own defaults. But approving something once doesn't mean it's approved forever — Claude should ask again next time.

## Setting it up

Step 1 — get a local copy of the source repo to copy text from (open Terminal for this one):
```bash
git clone https://github.com/brett6320/claude-code-baseline.git /tmp/ccb
```

Step 2 — open the policy files (in `/tmp/ccb/policies/`) in TextEdit or Finder, read the ones you want to adopt, and copy/paste the relevant rule text into your `~/.claude/CLAUDE.md` (open it as shown above). This is manual copy-paste, on purpose — you're choosing which rules to actually adopt, not blindly importing all of them.

Step 3 (optional) — keep the full reference material around for later:
```bash
mkdir -p ~/.claude/reference
cp -r /tmp/ccb/policies ~/.claude/reference/guardrails-policies
cp /tmp/ccb/GUARDRAILS.md ~/.claude/reference/
```

## Checking it worked

Start a new Claude Code session and ask it: "what are my guardrails?" — it should describe the attribution/commit/branch/merge rules back to you from what's in `~/.claude/CLAUDE.md`.
