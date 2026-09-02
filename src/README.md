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

## Release History

### v0.0.11 (2026-01-19)

Highlights:

- Add an `"invite"` field to the room sorting settings ([docs][Sorting Lists])
- Add `:space` commands for updating space hierarchy ([docs][Updating Space Hierarchy])
- New `mouse` configuration options to enable mouse scrolling ([docs][Mouse Support])
- Add `:replied` to go to the message the selected message replied to ([docs][Replying To A Message])
- Add `:forget` to forget all left rooms ([docs][Joining And Leaving Rooms])
- Indicate encryption state of room in messagebar ([docs][Encryption Status Indicator])
- Show state events in the timeline ([docs][Message Scrollback])
- Support per-thread receipts ([docs][Threads])
- Update to Rust Matrix SDK v0.14.0
- See [Release Notes][release-0.0.11] for the full list of changes!

### v0.0.10 (2024-08-21)

Highlights:

- Add a `:room dm set` command to mark rooms as DMs ([docs][Marking Direct Rooms])
- Set per-room notification levels ([docs][Configuring Room Notifications])
- Command to mark all rooms read ([docs][Browsing Unreads])
- Message slash commands ([docs][Message Slash Commands])
- Support for managing room aliases ([docs][Setting Room Aliases])
- Support for kicking users from rooms ([docs][Managing Room Membership])
- See [Release Notes][release-0.0.10] for the full list of changes!

### v0.0.9 (2024-03-29)

Highlights:

- Image previews for terminals w/ support ([docs][Image Previews])
- Support for threads ([docs][Threads])
- Unread indicators ([docs][Browsing Unreads])
- Support for notifications via terminal bell or desktop environment ([docs][Notifications])
- Added a `:editor` command for editing messages using `$EDITOR` ([docs][Sending])
- Mapping custom keybindings to macros ([docs][Custom Keybindings])
- Custom sorting for room and member lists ([docs][Sorting Lists])
- Import and exporting room keys ([docs][Exporting / Importing Keys])
- Switch to using TOML for configuration
- Update to Rust Matrix SDK v0.7.1
- See [Release Notes][release-0.0.9] for the full list of changes!

### v0.0.8 (2023-07-08)

Highlights:

- Add a `:leave` command to leave rooms ([docs][Joining And Leaving Rooms])
- New `username_display` configuration option for specifying how usernames are displayed ([docs][Settings])
- New `open_command` configuration option for specifying an external program for opening downloads ([docs][Settings])
- Restore layout on restart ([docs][Startup Layout])
- Update to Rust Matrix SDK v0.6.0
- See [Release Notes][release-0.0.8] for the full list of changes!

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
[release-0.0.8]: https://github.com/ulyssa/iamb/releases/tag/v0.0.8
[release-0.0.9]: https://github.com/ulyssa/iamb/releases/tag/v0.0.9
[release-0.0.10]: https://github.com/ulyssa/iamb/releases/tag/v0.0.10
[release-0.0.11]: https://github.com/ulyssa/iamb/releases/tag/v0.0.11

<!-- Documentation cross-references: -->
[Browsing Unreads]: ./rooms/browsing.md#browsing-unreads
[Configuring Room Notifications]: ./rooms/management.md#configuring-room-notifications
[Custom Keybindings]: ./configure.md#custom-keybindings
[Encryption Status Indicator]: ./e2ee/#encryption-status-indicator
[Exporting / Importing Keys]: ./e2ee/keys.md#exporting-importing-keys
[Image Previews]: ./configure.md#image-previews
[Joining And Leaving Rooms]: ./rooms/#joining-and-leaving-rooms
[Managing Room Membership]: ./rooms/admin.md#managing-room-membership
[Marking Direct Rooms]: ./rooms/management.md#marking-direct-rooms
[Message Scrollback]: ./messages/#message-scrollback
[Message Slash Commands]: ./messages/#message-slash-commands
[Mouse Support]: ./configure.md#mouse-support
[Notifications]: ./configure.md#notifications
[Replying To A Message]: ./messages/#replying-to-a-message
[Sending]: ./messages/#sending
[Setting Room Aliases]: ./rooms/admin.md#setting-room-aliases
[Settings]: ./settings.md#settings
[Sorting Lists]: ./configure.md#sorting-lists
[Startup Layout]: ./configure.md#startup-layout
[Threads]: ./messages/#threads
[Updating Space Hierarchy]: ../rooms/admin.md#updating-space-hierarchy
