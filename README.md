# Wozi public macOS setup

The short URL downloads a complete, temporary checkout of the standalone public
[PKGMacSetupPublic repository](https://github.com/wozi-x/PKGMacSetupPublic),
checks its shell entrypoints, and then runs `install.sh`. It does not authenticate
GitHub, download a private repository, or choose a configuration for you.

First prepare the reviewed controller prerequisites:

```sh
curl -fsSL https://wozi-x.github.io/mac |
  /bin/bash -p -s -- --prepare
```

Then preview and apply one complete public selection. For an Admin Mac:

```sh
curl -fsSL https://wozi-x.github.io/mac |
  /bin/bash -p -s -- --config examples/admin.yml --plan
curl -fsSL https://wozi-x.github.io/mac |
  /bin/bash -p -s -- --config examples/admin.yml --apply
```

For a development Mac, choose the complete example matching its purpose:

```sh
# iOS development
curl -fsSL https://wozi-x.github.io/mac |
  /bin/bash -p -s -- --config examples/ios-dev.yml --plan

# Web development
curl -fsSL https://wozi-x.github.io/mac |
  /bin/bash -p -s -- --config examples/web-dev.yml --plan
```

Run these commands from the ordinary administrator account without adding
`sudo`. `--prepare` has its own review and confirmation. `--plan` is offline,
does not change the Mac, and normally exits with status 3 because it is a
configuration-only preview. `--apply` observes the Mac, displays the concrete
scope, and asks for confirmation and normal macOS authorization.

For repeat use or a customized package selection, clone or download the public
repository, copy the closest example YAML, and run `./install.sh` from that
checkout. The public profiles are preferences, not credential permissions.
Private personal components, NAS settings, Wozi integration, and private Admin/
Dev selections remain in the separately prepared private setup repository.
