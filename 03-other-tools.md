# Other recommended tools

All via Homebrew unless noted.

## Core CLI

```bash
brew install git              # macOS ships an old one; get current
brew install gh               # GitHub CLI — PRs, issues, releases from terminal
brew install jq                # JSON in shell pipelines
brew install ripgrep           # fast grep (rg)
brew install fzf               # fuzzy finder, shell history search
brew install wget curl
```

## Terminal

```bash
brew install --cask iterm2     # or Warp: brew install --cask warp
```

## Runtimes / version managers

```bash
brew install nvm               # Node version manager
# or: brew install node        # just latest Node
brew install pyenv              # Python version manager
```

## Claude Code

```bash
brew install --cask claude-code
# or: npm install -g @anthropic-ai/claude-code
```

## Containers

```bash
brew install --cask docker      # Docker Desktop
# or: brew install colima docker  # lighter, CLI-only
```

## Nice-to-haves

```bash
brew install --cask rectangle   # window management
brew install --cask raycast     # Spotlight replacement, launcher
brew install htop               # process viewer
```

## Sanity check

```bash
brew doctor
git --version && gh --version && code --version
```
