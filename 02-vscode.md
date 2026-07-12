# VS Code

## Install

```bash
brew install --cask visual-studio-code
```

## Enable `code` CLI

Usually wired by the cask automatically. If not: open VS Code → Cmd+Shift+P → "Shell Command: Install 'code' command in PATH".

Verify:
```bash
code --version
```

## Recommended extensions

```bash
code --install-extension eamodio.gitlens
code --install-extension esbenp.prettier-vscode
code --install-extension dbaeumer.vscode-eslint
code --install-extension ms-vscode-remote.remote-containers
code --install-extension editorconfig.editorconfig
```

Add language-specific ones as needed (Python, Go, etc.) per project.

## Settings sync

Sign in with GitHub/Microsoft account (bottom-left gear icon → "Turn on Settings Sync") to carry settings/extensions/keybindings across machines.
