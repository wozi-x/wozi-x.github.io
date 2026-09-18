# wozi-x macOS bootstrap

Run the installer on a new Mac:

```bash
curl -fsSL https://wozi-x.github.io/mac | /bin/bash -p
```

Run from Terminal using your administrator account, without adding `sudo` to
the command. Enter your Mac login password when the installer asks for it.

The `/mac` endpoint downloads the complete canonical installer from the public
[PKGMacSetupPublic repository](https://github.com/wozi-x/PKGMacSetupPublic),
checks its shell syntax, and only then executes it.

Review the installer before running it. It installs or updates Homebrew, Chrome,
1Password, the ChatGPT desktop app with Codex, and GitHub CLI; authenticates
GitHub; then clones or updates PKGMacSetup and starts standard setup. Standard
setup skips Mac App Store, private SMB, and DEVONthink database-restore tasks.
