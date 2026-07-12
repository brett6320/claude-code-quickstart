# Homebrew

## What it is

Homebrew is a tool that installs other software for you by typing one line instead of hunting for a download link, running an installer, dragging to Applications, etc. Most other guides in this series use it. There's no windowed app for Homebrew itself — it only works from Terminal, so this is one step you can't avoid via clicking.

## Step 1 — Open Terminal

- Press `Cmd + Space` to open Spotlight search.
- Type `Terminal` and press Return.
- A window opens with a blinking cursor waiting for text. This is normal — it's not broken, it's just plain text instead of buttons.

## Step 2 — Install Homebrew

Copy this whole line, paste it into the Terminal window (Cmd+V), then press Return:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

What happens next:
- It may ask for your Mac's login password. Type it — nothing will appear on screen as you type, that's expected (it's hidden for privacy). Press Return when done.
- It downloads and sets things up. Takes a few minutes. Wait for it to return you to a normal prompt (a line ending in `$` or `%` with nothing after it).

## Step 3 — One more one-time step

At the end, the installer prints 1-2 lines starting with `echo` — it wants you to add Homebrew to your PATH (this just means "so your Mac knows where to find it"). Copy the lines it printed for you specifically. If you're on a newer Mac (Apple Silicon / M1/M2/M3/M4), they'll look like this — paste both lines, one at a time, pressing Return after each:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

(If you have an older Intel Mac, the path will say `/usr/local` instead of `/opt/homebrew` — use whatever the installer actually printed.)

## Step 4 — Check it worked

```bash
brew doctor
```

If it prints "Your system is ready to brew," you're done. If it lists warnings, that's usually fine to ignore for now — only worry if a later step actually fails.

## Using it later

Any time another guide says `brew install something`, that means: open Terminal, paste that exact line, press Return.

- `brew install <name>` — installs a command-line tool
- `brew install --cask <name>` — installs a normal windowed app (same as dragging a .app to Applications, just automated)
- `brew update && brew upgrade` — keeps everything current, safe to run occasionally
