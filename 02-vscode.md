# VS Code

## What it is

VS Code (Visual Studio Code) is a free code editor — a text editor built for writing and reading code, with helpful extras like error highlighting and file navigation.

## Easiest way to install (no Terminal needed)

1. Go to https://code.visualstudio.com in your browser.
2. Click the big "Download for macOS" button.
3. Open the downloaded file (it'll be in your Downloads folder, named something like `VSCode-darwin-universal.zip`) — double-click it to unzip, giving you a `Visual Studio Code.app`.
4. Drag that app into your `Applications` folder.
5. Double-click it in Applications to open it — first time, macOS may ask "are you sure you want to open this app downloaded from the internet?" — click Open.

That's it — no Terminal required for this one.

## Alternative: install via Homebrew (if you already did the [Homebrew guide](01-homebrew.md))

Open Terminal and paste:

```bash
brew install --cask visual-studio-code
```

Same end result as the manual download — just automated.

## Optional: let VS Code open files from Terminal

If you plan to use Terminal at all (later guides do), this lets you type `code somefile.txt` to open a file in VS Code instead of clicking through Finder. Not required — skip if this doesn't sound useful to you.

1. Open VS Code.
2. Press `Cmd + Shift + P` — this opens VS Code's command palette (a searchable menu, not Terminal).
3. Type: `Shell Command: Install 'code' command in PATH` and press Return when it appears.

Check it worked by opening Terminal and typing:
```bash
code --version
```
If it prints a version number, it worked.

## Recommended extensions

Extensions add features to VS Code — click-installable from inside the app:

1. Open VS Code.
2. Click the square icon in the left sidebar (looks like 4 overlapping squares) — this is the Extensions panel.
3. Search for and click "Install" on each of these:
   - **GitLens** — shows who changed what line of code, and when
   - **Prettier** — auto-formats your code so it looks consistent
   - **ESLint** — flags likely bugs in JavaScript/TypeScript as you type
   - **Dev Containers** — lets a project run in an isolated environment
   - **EditorConfig** — keeps formatting consistent across a team

Add other extensions later as specific projects need them (e.g. a Python extension for Python projects).

## Optional: sync your settings across Macs

Click the gear icon (bottom-left corner) → "Turn on Settings Sync" → sign in with a Microsoft or GitHub account. This carries your settings/extensions/keybindings to any other Mac you sign into.
