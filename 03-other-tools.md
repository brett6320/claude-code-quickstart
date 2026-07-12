# Other recommended tools

A menu, not a checklist — install only what sounds useful to you. Everything here needs [Homebrew](01-homebrew.md) installed first, and everything runs from Terminal (`Cmd + Space` → type `Terminal` → Return) unless marked "GUI app."

For each, paste the command into Terminal and press Return.

## Command-line basics

- **git** — tracks changes to code over time, lets you undo mistakes and collaborate. macOS ships an old version; this gets you current:
  ```bash
  brew install git
  ```
- **gh** (GitHub CLI) — lets you create/manage GitHub pull requests and issues from Terminal instead of the browser:
  ```bash
  brew install gh
  ```
- **jq** — reformats and filters JSON data so it's readable in Terminal. Only useful if you'll be scripting things:
  ```bash
  brew install jq
  ```
- **ripgrep** (command: `rg`) — searches through file contents very fast, better than the built-in `grep`:
  ```bash
  brew install ripgrep
  ```
- **fzf** — lets you fuzzy-search your Terminal command history and files interactively:
  ```bash
  brew install fzf
  ```

## Terminal app upgrade (GUI apps)

macOS's built-in Terminal app is fine, but these are nicer if you'll use it a lot:

```bash
brew install --cask iterm2
```
or
```bash
brew install --cask warp
```
Install either one, open it from Applications like any other app — it replaces (doesn't remove) the built-in Terminal.

## Programming language version managers

Only relevant if you're doing software development in these languages:

- **nvm** — lets you switch between different versions of Node.js per-project:
  ```bash
  brew install nvm
  ```
  (Or, if you just want one current version of Node with no version-switching: `brew install node`)
- **pyenv** — same idea, for Python:
  ```bash
  brew install pyenv
  ```

## Claude Code

An AI coding assistant that runs in Terminal.

```bash
brew install --cask claude-code
```

## Docker (containers)

Lets you run isolated, reproducible environments — useful if a project asks for it.

```bash
brew install --cask docker
```
This installs Docker Desktop (a GUI app that appears in Applications, alongside a `docker` Terminal command). Open it once from Applications to finish setup.

## Nice-to-have GUI apps

- **Rectangle** — snap windows to half/quarter of the screen with keyboard shortcuts:
  ```bash
  brew install --cask rectangle
  ```
- **Raycast** — a faster replacement for Spotlight search:
  ```bash
  brew install --cask raycast
  ```
- **htop** — shows what's using your CPU/memory, Terminal-based:
  ```bash
  brew install htop
  ```

## Check what you've installed

```bash
brew list
```
Prints everything Homebrew has installed so far.
