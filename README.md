# wozi-x macOS bootstrap

Run the installer on a new Mac:

```bash
curl -fsSL https://wozi-x.github.io/mac | /bin/bash -p
```

Run from Terminal using your administrator account, without adding `sudo` to
the command. Enter your Mac login password when the installer asks for it.

The `/mac` endpoint downloads the complete canonical
[installer Gist](https://gist.github.com/wozi-x/3a9aea7de1296af6147bacaaae96f6fb),
checks its shell syntax, and only then executes it.

Review the Gist before running it. It prepares Command Line Tools, Homebrew,
and GitHub CLI, then offers **Base**, **Dev**, and **Admin**. Existing
installations are reused.

Base downloads a reviewed immutable revision of
[PKGMacSetupPublic](https://github.com/wozi-x/PKGMacSetupPublic). It installs a
small workstation baseline and selected macOS preferences without a GitHub
account or sign-in. It never downloads the Dev/Admin repository. Dev and Admin
reuse a working GitHub login or guide browser sign-in, require repository access, and
run its existing `./setup.sh` or `./setup.sh --admin-mac`; App Store and private
storage remain separate stages.

To use an existing local Base configuration directory, pass its absolute path
to the shell running the starter, then select Base:

```sh
curl -fsSL https://wozi-x.github.io/mac |
  PKGMACSETUP_BASE_CONFIG_DIR="$HOME/mac-setup" /bin/bash -p
```

That directory stays local. Its Brewfile replaces Base's default package list;
see the public repository for supported preferences and dotfile fragments.
App Store purchases require manual sign-in when selected locally.
