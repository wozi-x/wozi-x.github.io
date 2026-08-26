# wozi-x macOS bootstrap

Run the installer on a new Mac:

```bash
curl -fsSL wozi-x.github.io|sh
```

The site root delegates to `/mac`, which downloads and runs the canonical
[installer Gist](https://gist.github.com/wozi-x/3a9aea7de1296af6147bacaaae96f6fb).

The explicit endpoint remains available:

```bash
curl -fsSL https://wozi-x.github.io/mac | bash
```

Review the Gist before running it. It installs or updates Homebrew, Chrome,
1Password, the ChatGPT desktop app with Codex, and GitHub CLI; authenticates
GitHub; then clones or updates PKGMacSetup and starts the full setup.
