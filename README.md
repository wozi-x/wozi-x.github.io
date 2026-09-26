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
Once a route is selected, 1Password Desktop is installed or reused before
setup continues, including before Dev/Admin GitHub sign-in.

Base downloads a reviewed immutable revision of
[PKGMacSetupPublic](https://github.com/wozi-x/PKGMacSetupPublic). It installs a
small workstation baseline and selected macOS preferences without a GitHub
account or GitHub sign-in. Its default Brewfile includes 1Password and
Amphetamine through the Mac App Store. Interactive setup opens the account
apps and waits for you: press Return when ready, s to skip, or q to quit.
It never downloads the Dev/Admin repository. Dev and Admin
reuse a working GitHub login or guide browser sign-in, require repository access, and
pause for account preparation, and run
`./setup.sh` or `./setup.sh --admin-mac`. Setup offers App Store installation
in the same run and waits while you sign in. Private storage remains a
separate, explicit stage.
Skipping private account preparation defers enrollment and signing for that run.
Skipping Base App Store work is reported as deferred without failing setup.
App Store installation may require the Mac login password for administrator
authorization even when the Apple Account is already signed in.

To use an existing local Base configuration directory, pass its absolute path
to the shell running the starter, then select Base:

```sh
curl -fsSL https://wozi-x.github.io/mac |
  PKGMACSETUP_BASE_CONFIG_DIR="$HOME/mac-setup" /bin/bash -p
```

That directory stays local. Its Brewfile replaces Base's default package list;
see the public repository for supported preferences and dotfile fragments.
App Store apps require manual sign-in, including the default Amphetamine entry.
