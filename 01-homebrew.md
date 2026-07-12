# Homebrew

Package manager for macOS. Install first — everything else in this guide assumes it exists.

## Install

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Installer prints next steps at end — usually add brew to PATH:

**Apple Silicon** (`/opt/homebrew`):
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

**Intel** (`/usr/local`):
```bash
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/usr/local/bin/brew shellenv)"
```

## Verify

```bash
brew doctor
brew --version
```

## Daily use

```bash
brew install <formula>       # CLI tool
brew install --cask <app>    # GUI app
brew update && brew upgrade  # keep current
brew list                    # what's installed
```
