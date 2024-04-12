# Introduction

__iamb__ is a terminal-based client for [Matrix] for the Vim addict. You can
edit messages, navigate windows and manage tabs in the same ways that your
fingers are used to from your favorite text editor!

![Example Usage](/static/images/iamb-demo.gif)

## Features

- Threads, spaces, E2EE, and read receipts
- Image previews in terminals that support it (sixels, Kitty, and iTerm2), or using pixelated blocks for those that don't
- Notifications via terminal bell or desktop environment
- Creating, joining, and leaving rooms
- Sending and accepting room invitations
- Editing, redacting, and reacting to messages
- Custom keybindings
- Multiple profiles

## Reading This Documentation

This documentation indicates keybindings using the following conventions:

- Named keys are shown between angle brackets; for example, `<Space>` is the
  space bar.
- Modifiers like the control key or shift are shown with their combining key
  between brackets; for example, `<C-W>` is Ctrl-W and `<S-Tab>` is Shift+Tab.
- Sequences of keys to be pressed are shown in the order to press them; for
  example, `<C-W>gf` indicates that you should type Ctrl-W, then g, and finally f.

## Contributing

__iamb__ is free and open source. You can find the source code, report bugs and
request features on [GitHub][iamb].

If you find a mistake in this documentation, you can report it or submit a pull
request at the [iamb.chat] GitHub repository. 

Most of the Vim emulation in __iamb__ comes from the [modalkit] crate. If you
find a bug in text editing, window management, or need a Vim keybinding added,
you can file an issue there.

## Join us on Matrix!

Please feel free to join us in:

- [#iamb-users:0x.badd.cafe] for discussing using __iamb__
- [#iamb-dev:0x.badd.cafe] for discussing developing __iamb__

Both of these are in the [#iamb:0x.badd.cafe] space.

## License

iamb and its documentation are released under the [Apache License, Version 2.0].

[Apache License, Version 2.0]: https://github.com/ulyssa/iamb/blob/master/LICENSE
[#iamb:0x.badd.cafe]: https://matrix.to/#/#iamb:0x.badd.cafe
[#iamb-dev:0x.badd.cafe]: https://matrix.to/#/#iamb-dev:0x.badd.cafe
[#iamb-users:0x.badd.cafe]: https://matrix.to/#/#iamb-users:0x.badd.cafe
[iamb]: https://github.com/ulyssa/iamb/
[iamb.chat]: https://github.com/ulyssa/iamb.chat/
[Matrix]: https://matrix.org/
[modalkit]: https://github.com/ulyssa/modalkit
