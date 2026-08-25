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

Review the Gist before running it. It installs or updates Homebrew, Codex CLI,
the ChatGPT desktop app with Codex, and GitHub CLI. The desktop app is skipped
on Intel Macs because OpenAI's current macOS build requires Apple Silicon.
