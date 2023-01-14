# Introduction

__iamb__ is a terminal-based client for [Matrix] for the Vim addict. You can
edit messages, navigate windows and manage tabs in the same ways that your
fingers are used to you from your favorite text editor!

## Reading This Documentation

This documentation indicates keybindings using the following conventions:

- The control key is shown with a leading caret; for example, `^W` is Ctrl-W.
- Named keys are shown between angle brackets; for example, `<Space>` is the
  space bar.
- Sequences of keys to be pressed are shown in the order to press them; for
  example, `^Wgf` indicates that you should type Ctrl-W, then g, and finally f.

## Contributing

__iamb__ is free and open source. You can find the source code, report bugs and
request features on [GitHub][iamb].

If you find a mistake in this documentation, you can report it or submit a pull
request at the [iamb.chat] GitHub repository. 

Most of the Vim emulation in __iamb__ comes from the [modalkit] crate. If you
find a bug in text editing, window management, or need a Vim keybinding added,
you can file an issue there.

## License

iamb and its documentation are released under the [Apache License, Version 2.0].

[Apache License, Version 2.0]: https://github.com/ulyssa/iamb/blob/master/LICENSE
[iamb]: https://github.com/ulyssa/iamb/
[iamb.chat]: https://github.com/ulyssa/iamb.chat/
[Matrix]: https://matrix.org/
[modalkit]: https://github.com/ulyssa/modalkit
