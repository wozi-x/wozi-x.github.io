# wozi-x macOS bootstrap

Run the installer on a new Mac:

```bash
curl -fsSL https://wozi-x.github.io/mac | /bin/bash -p
```

To skip the menu, choose `--base`, `--dev`, or `--admin`:

```sh
curl -fsSL https://wozi-x.github.io/mac | /bin/bash -p -s -- --dev
```

Use `--status` instead to report the last setup role and check key installed
features without installing or signing in. Older Macs without a setup receipt
report an unknown role; feature presence does not prove every stage completed.
Custom configurations may omit listed features.

Run from Terminal using your administrator account, without adding `sudo` to
the command. Enter your Mac login password when the installer asks for it.

The `/mac` endpoint downloads the complete canonical
[installer Gist](https://gist.github.com/wozi-x/3a9aea7de1296af6147bacaaae96f6fb),
checks its shell syntax, and only then executes it.

Review the Gist before running it. Choose **Base**, **Dev**, or **Admin** first;
it then prepares Command Line Tools, Homebrew, and GitHub CLI. Existing
installations are reused.
Command Line Tools installation is detected automatically. Return rechecks and
`q` quits the wait. Local Dev/Admin stage failures offer Return to retry that
stage, `s` to continue with other stages, and `q` to quit.
Once a route is selected, 1Password Desktop is installed or reused before
setup continues, including before Dev/Admin GitHub sign-in.

Base downloads a reviewed immutable revision of
[PKGMacSetupPublic](https://github.com/wozi-x/PKGMacSetupPublic). It installs a
small workstation baseline and selected macOS preferences without a GitHub
account or GitHub sign-in. Its default Brewfile includes 1Password and
Amphetamine through the Mac App Store. Interactive setup opens 1Password after
a new installation and the App Store when apps are missing: press Return when
ready, s to skip, or q to quit. Existing 1Password installations skip that pause.
It never downloads the Dev/Admin repository. Dev and Admin
reuse a working GitHub login or guide browser sign-in, require repository access, and
run `./setup.sh` or `./setup.sh --admin-mac`. Setup offers App Store installation
in the same run and pauses for sign-in only when its selected work is pending or
could not be checked. Enrollment preparation is requested only when enrollment
is missing after runner preparation. Interactive Admin setup also offers enabled
private storage after signing: confirm NAS access, save its password in Finder,
close DEVONthink, then press Return. Use `s` to defer or `q` to quit. Dev, remote
and unattended runs do not request private storage.
Skipping enrollment preparation defers enrollment and signing for that run.
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
