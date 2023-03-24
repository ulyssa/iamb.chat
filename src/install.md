# Installation

## From a package manager

### Arch Linux

Using your preferred [AUR helper], you can install `iamb-git`. For example,
using `paru`:

```
paru iamb-git
```

### NetBSD

```
pkgin install iamb
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
iamb 0.0.7
```

[AUR helper]: https://wiki.archlinux.org/title/AUR_helpers
[crates.io]: https://crates.io/crates/iamb
[GitHub]: https://github.com/ulyssa/iamb
[Releases]: https://github.com/ulyssa/iamb/releases/
