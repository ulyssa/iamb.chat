# Installation

## From a package manager

Several community members have taken care of setting up packages for their
preferred operating systems and distributions. If you don't see your system
on this page, try checking [repology] to see whether one exists for your
system.

### Arch Linux

Using your preferred [AUR helper], you can install `iamb-git`. For example,
using `paru`:

```
paru iamb-git
```

### FreeBSD

On FreeBSD a package is available from the official repositories. To install it
simply run:

```
pkg install iamb
```

### macOS

On macOS a [package][homebrew] is available in Homebrew's repository. To
install it simply run:

```
brew install iamb
```

### NetBSD / pkgsrc

On NetBSD (or any other system [with pkgsrc available][pkgsrc]), you can
install the `iamb` package:

```
pkgin install iamb
```

### NixOS

There is an `iamb` package available in the 23.11 channel, or, if you have
[enabled flakes] in Nix, you can install __iamb__ from the Git repository via:

```
nix profile install "github:ulyssa/iamb/latest"
```

You can replace `latest` with a branch or specific version tag name if you want
to install something besides the most recent release (e.g. `main` or `v0.0.8`).

### openSUSE Tumbleweed

On openSUSE Tumbleweed a [package][openSUSE] is available from openSUSE Build
Service (OBS). You can install it using OBS Package Installer:

```
opi iamb
```

### Snap

A snap is available for Linux distributions [which support it][install-snap]:

```
snap install iamb
```

## GitHub Releases

You can find binaries built for x86\_64 Linux from the [Releases] page on GitHub.

## From crates.io

You can install the most recently published version of __iamb__ from
[crates.io] using `cargo`: 

```
$ cargo install --locked iamb
```

This will install the `iamb` binary to `~/.cargo/bin/`, which you should then
place in your `$PATH`.

## From Git Repository

If you are working on __iamb__ or need a change that has not yet been
published, you can clone the source from [GitHub] and build from that:

```
$ git clone https://github.com/ulyssa/iamb.git
$ cd iamb
$ cargo build --release
$ ./target/release/iamb --version
iamb 0.0.9 (82645c8)
```

[AUR helper]: https://wiki.archlinux.org/title/AUR_helpers
[crates.io]: https://crates.io/crates/iamb
[enabled flakes]: https://nixos.wiki/wiki/Flakes#Enable_flakes
[GitHub]: https://github.com/ulyssa/iamb
[homebrew]: https://formulae.brew.sh/formula/iamb#default
[install-snap]: https://snapcraft.io/docs/installing-snapd
[openSUSE]: https://build.opensuse.org/package/show/home%3Asmolsheep/iamb
[pkgsrc]: https://pkgsrc.smartos.org/
[Releases]: https://github.com/ulyssa/iamb/releases/
[repology]: https://repology.org/project/iamb/versions
