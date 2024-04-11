# Development

## Setting Up Your Environment

In order to work on and build __iamb__ locally, you will need:

- `stable` Rust toolchain with `clippy` installed
- `nightly` Rust toolchain with `rustfmt` installed

You can install the necessary Rust dependencies using [rustup]:

```shell
rustup toolchain install stable --component clippy
rustup toolchain install nightly --component rustfmt
```

You will also likely want to use [rust-analyzer] during your development. Refer
to its documentation for help on setting it up in your preferred editor.

## Programming In Rust

If you are new to Rust, some helpful resources to learn or refer to are:

- [The Rust Book](https://doc.rust-lang.org/book/) (or [an alternative version](https://rust-book.cs.brown.edu/) with quizzes and visualizations)
- [The Rust Standard Library](https://doc.rust-lang.org/std/index.html) documentation
- [Asynchronous Programming in Rust](https://rust-lang.github.io/async-book/)
- [Rust Playground](https://play.rust-lang.org/) is helpful for trying small examples and learning how things work

You can find more resources on [the Rust website](https://www.rust-lang.org/learn).

At some point while working on __iamb__, you will have to touch one of its
dependencies. Some of the libraries whose docs you may need are:

- [matrix-sdk]
- [modalkit]
- [modalkit-ratatui]
- [ratatui] (see also the [ratatui book], which includes small demos and How-Tos)
- [tokio] (see also the [tokio tutorial])

## Building, Formatting and Testing

The commands you will want to run the most are:

- `cargo check` to run the type checker and borrow checker
- `cargo build` to build a debug binary (outputs to `target/debug/iamb`)
- `cargo test` to run the unit tests
- `cargo clippy` to run lints and get suggestions for simplifying code
- `cargo +nightly fmt` to apply the crate's standard formatting to your changes

Once you have something you're happy with, you can run `cargo build --release`
to get a release binary. If you have a machine with plenty of RAM, you can use
`cargo build --profile release-lto` to build a smaller, optimized binary using
Link-Time Optimization.

## Making a Pull Request

If you are unfamiliar with Git or GitHub, refer to the [Git Book] or
[Creating a pull request] to get started.

If you want feedback while you're still working on something, then
please open a Draft Pull Request, so that someone can take a look.

## Getting Help

There are several different places you can reach out for help:

- [#iamb-dev:0x.badd.cafe] to discuss in a Matrix room
- File a [GitHub issue] to discuss your change (or comment on an existing one)
- Open a Draft Pull Request to show and discuss code

[#iamb-dev:0x.badd.cafe]: https://matrix.to/#/#iamb-dev:0x.badd.cafe
[Creating a pull request]: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request
[Git Book]: https://git-scm.com/book/en/v2
[GitHub issue]: https://github.com/ulyssa/iamb/issues
[matrix-sdk]: https://docs.rs/matrix-sdk/latest/matrix_sdk/
[modalkit]: https://docs.rs/modalkit/latest/modalkit/
[modalkit-ratatui]: https://docs.rs/modalkit-ratatui/latest/modalkit_ratatui/
[ratatui]: https://docs.rs/ratatui/latest/ratatui/
[ratatui book]: https://ratatui.rs/introduction/
[rustup]: https://rustup.rs/
[rust-analyzer]: https://rust-analyzer.github.io/
[tokio]: https://docs.rs/tokio/latest/tokio/
[tokio tutorial]: https://tokio.rs/tokio/tutorial
