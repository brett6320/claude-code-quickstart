# Caveman skill

Source: [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman)

Ultra-compressed Claude Code communication mode — cuts ~65-75% tokens, keeps technical accuracy. Levels: lite, full (default), ultra, wenyan-*.

**Status on this machine: already global, already default-on.** `~/.claude/settings.json` has a `SessionStart` hook that injects "caveman mode active, full level" into every session's context, regardless of project or prompt wording. Confirmed working — this doc was written under it.

```json
"hooks": {
  "SessionStart": [
    { "hooks": [ { "type": "command",
      "command": "printf '%s' '{\"hookSpecificOutput\":{\"hookEventName\":\"SessionStart\",\"additionalContext\":\"Caveman mode is active by default this session (full level)...\"}}'"
    } ] }
  ]
}
```

This approach (hook-injected context) achieves global default-on more directly than installing the marketplace plugin — no per-session `/caveman` trigger needed, works before the skill/plugin system even loads. Keep it as-is; no action needed. Section below is the plugin-based alternative if you ever reinstall from scratch on a new machine.

## Alternative — global, plugin marketplace (auto-activates every session)

```bash
claude plugin marketplace add JuliusBrussee/caveman
claude plugin install caveman@caveman
```

This is a **global** Claude Code plugin (lives under `~/.claude`, not per-repo) — it auto-activates for Claude Code (per the repo's agent table: "Auto-activates? Yes"). No `/caveman` needed each session once installed.

## Force it on every session without exception

Plugin auto-activation triggers on natural-language cues ("caveman mode", "talk like caveman") or session hooks. To guarantee full-level caveman on **every** session regardless of prompt wording, add a standing line to your global `~/.claude/CLAUDE.md`:

```markdown
## Caveman mode
Caveman mode active every session, full level, by default. Terse: drop articles/filler/hedging,
fragments OK, short synonyms, keep all technical substance and exact code/errors. Stays active
until user says stop caveman or normal mode. Write code/commits/PRs normally (not caveman).
```

This is what's already driving this session (see the SessionStart hook context) — copying it into your permanent `~/.claude/CLAUDE.md` makes it permanent instead of one-off.

## Verify

Open new session, don't say anything caveman-related — response should already be terse/fragment style. Say "stop caveman" to confirm it can toggle off.

## Uninstall

```bash
claude plugin uninstall caveman@caveman
```
