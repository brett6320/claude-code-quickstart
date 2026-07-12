# Caveman skill

Only relevant if you use Claude Code (an AI coding assistant that runs in Terminal). Skip this if that's not you.

Source: [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman)

## What this is, in plain terms

By default, Claude Code writes in full sentences. "Caveman mode" tells it to respond in short, dropped-article fragments instead ("File not found" instead of "It looks like the file could not be found") — same technical content, fewer words, which means it costs less and responds faster. It never affects the actual code/commits it writes, only its chat replies to you.

## Recommended setup: make it automatic every session

This uses a Claude Code "hook" — a small script Claude Code runs automatically at certain moments (here: every time a session starts). You'll edit one file.

1. Open the settings file. In Terminal:
   ```bash
   open -a TextEdit ~/.claude/settings.json
   ```
   (`~/.claude` is a hidden folder in your home directory — if you'd rather browse to it in Finder, press `Cmd+Shift+G`, type `~/.claude`, Return.)

2. This file is in JSON format (a structured text format with `{ }` braces — don't worry about understanding all of it). Add a `"hooks"` section like this. If the file already has a `"hooks"` key, add the `SessionStart` block inside its existing braces instead of duplicating the key:
   ```json
   {
     "hooks": {
       "SessionStart": [
         {
           "hooks": [
             {
               "type": "command",
               "command": "printf '%s' '{\"hookSpecificOutput\":{\"hookEventName\":\"SessionStart\",\"additionalContext\":\"Caveman mode is active by default this session (full level). Respond terse like smart caveman: drop articles/filler/hedging, fragments OK, short synonyms, keep all technical substance and exact code/errors. Stays active until the user says stop caveman or normal mode. Write code/commits/PRs normally.\"}}'"
             }
           ]
         }
       ]
     }
   }
   ```
3. Save the file (Cmd+S) and close it.
4. Start a new Claude Code session — it should reply in terse fragments immediately, with no need to say anything about caveman mode.

To turn it off in a given conversation, just tell Claude "stop caveman" or "normal mode."

## Alternative: install as a plugin instead

This is a different approach — installing caveman as a Claude Code plugin rather than a hook. Skip this if you did the hook setup above; you don't need both.

In Terminal:
```bash
claude plugin marketplace add JuliusBrussee/caveman
claude plugin install caveman@caveman
```

Per the source repo, this auto-activates for Claude Code — no extra step needed. If your Claude Code version doesn't auto-activate it, say "caveman mode" or "/caveman" once per session to turn it on.

## Removing it

- If you used the plugin: `claude plugin uninstall caveman@caveman`
- If you used the hook: open `~/.claude/settings.json` again and delete the `SessionStart` block you added.
