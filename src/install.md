# Installation

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
iamb 0.0.6
```

[crates.io]: https://crates.io/crates/iamb
[GitHub]: https://github.com/ulyssa/iamb
