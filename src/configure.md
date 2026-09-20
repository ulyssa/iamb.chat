# Configuration

__iamb__ is configurable via a TOML configuration file located in the
configuration directory. By default, the configuration directory is determined
by [dirs::config_dir] (on macOS, `XDG_CONFIG_HOME` is prioritized if set,
defaulting otherwise to `~/Library/Application Support`), but you can override
it at startup with the `-C` command-line flag. To see what changing these
options away from their defaults can look like, see [config.example.toml]
in the repository.

## Profiles

You can configure a Matrix account in your `config.toml` by creating a
`profiles` subsection with a `user_id` field specifying your account:

```toml
[profiles.user]
user_id = "@user2:example.com"
```

When you start __iamb__ for the first time, it will ask you whether you want to
log in with a password (enter `p` to select), or SSO (enter `s` to select). If
you choose SSO, then a page will open in your browser to go through the SSO
authentication flow.

### Multiple Profiles

You can create multiple profiles for different accounts or settings by adding
additional subsections to the `profiles` section:

```toml
default_profile = "user"

[profiles.admin]
user_id = "@user1:example.com"

[profiles.user]
user_id = "@user2:example.com"
```

With the `default_profile` field set, __iamb__ will default to using the
`user` profile at startup. You can manually specify what you want via the `-P`
flag. For example:

```
$ iamb -P admin
Logging in for @user1:example.com...
```

If no profile is specified on the command line and `default_profile` is not set
in your configuration, __iamb__ will interactively prompt you at startup to
select a profile.

### Per-Profile Configuration

Several of the sections that you can place under the global configuration can
also be placed within profile configurations to achieve per-profile values:

- `aliases`
- `dirs`
- `layout`
- `macros`
- `settings`

Per-profile values will be merged on top of the global values. For example:

```toml
[profiles.user.layout]
style = "restore"

[profiles.admin.layout]
style = "new"
```

### Explicit Homeserver URLs

If your homeserver is located on a different domain than the server part of the
`user_id` and you don't have a [`/.well-known`][well_known_entry] entry, then
you can explicitly specify the homeserver URL to use:

```toml
default_profile = "user"

[profiles.admin]
user_id = "@user1:example.com"
url = "https://example.com"

[profiles.user]
user_id = "@user2:example.com"
url = "https://example.com"
```

## Settings

| Name                         | Default              | Description                                                                                                                          |
| ---------------------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `auto_focus_message_bar`     | `false`              | Whether to automatically focus the message bar when entering Insert mode in a room window.                                           |
| `cache_policy`               |                      |                                                                                                                                      |
| `default_room`               |                      | A default room name or username to open at startup, in place of showing the welcome screen.                                          |
| `default_markup`             | `"markdown"`         | The default markup format for interpreting text in the message bar. Valid values are `"markdown"`, `"html"`, and `"plaintext"`.      |
| `default_register`           | `"`                  | The default register to use for yanking, deleting and pasting.                                                                       |
| `default_split`              | `"horizontal"`       | The default direction in which to split windows. Valid values are `"horizontal"` and `"vertical"`.                                   |
| `default_via"`               | `["matrix.org"]`     | The default servers to use when attempting to join a new room if your homeserver is unaware of the room and cannot resolve the alias.|
| `encryption`                 |                      | Configures how information related to room encryption is displayed in the UI. See [Encryption](#encryption) below.                   |
| `external_edit_file_suffix`  | `.md`                | The file suffix to use when creating temporary files with message contents for `:edit`. (Usually you want the default `.md` for syntax highlighting.) |
| `ignorecase`                 | `false`              | Configures whether to disable case sensitivity for the regular expressions entered in the search bar.                                |
| `image_preview`              | (unset)              | Configures displaying image attachments for terminals that support previewing images. See [Image Previews](#image-previews) below.   |
| `input_prompt`               | (unset)              | Configures a value to display as the prompt in the message bar.                                                                      |
| `log_level`                  | `"info"`             | Configures the minimum log level. Valid values are `"trace"`, `"debug"`, `"info"`, `"warn"` or `"error"`.                            |
| `max_log_files`              | `7`                  | Configures how many days worth of logs to keep. Setting this to `0` disables automatically deleting the files.                       |
| `message_user_color`         | `false`              | Whether to color entire messages using the same color used for the sender's username and display name.                               |
| `message_shortcode_display`  | `false`              | Whether to replace Emojis in message bodies with their shortcodes.                                                                   |
| `mouse`                      | (unset)              | Configures mouse scroll support in the message scrollback. See [Mouse Support](#mouse-support) below.                                |
| `normal_after_send`          | `false`              | Whether to automatically reset the Vim mode to Normal mode after sending a message.                                                  |
| `notifications`              | (unset)              | Whether to generate desktop notifications for messages sent to rooms not currently being viewed. See [Notifications](#notifications) |
| `open_command`               | (unset)              | Configures a command to use for opening downloads instead of the default. (e.g., `["my-open", "--file"]` to run a custom script      |
| `proxy`                      | (unset)              | Configures proxying requests to the homeserver through SOCKS5 or an HTTPS proxy. See [Proxying](#proxying) below.                    |
| `reaction_display`           | `true`               | Whether to display message reactions. You can use this or `reaction_shortcode_display` if your terminal doesn't show Emojis well.    |
| `reaction_shortcode_display` | `false`              | Whether to show the shortcode value instead of the Emoji for reactions. If no shortcode is available, then it won't be displayed.    |
| `read_receipt_display`       | `true`               | Whether to display read receipts next to messages in the room scrollback.                                                            |
| `read_receipt_send`          | `true`               | Whether to send read receipts for viewed rooms.                                                                                      |
| `read_receipt_trigger`       | `"focused"`          | When to send read receipts for viewed rooms. Valid values are `"focused"`, `"visible"`, `"scrollback"`, and `"message"`.             |
| `request_timeout`            | 120                  | How long to wait in seconds before timing out requests to the homeserver.                                                            |
| `sort`                       |                      | Configures how to sort the lists in different windows like `:rooms` or `:members`. See [Sorting Lists](#sorting-lists) below.        |
| `ssl_verify`                 | `true`               | Configures whether the homeserver's certificate should be rejected when invalid, to protect against insecure connections.            |
| `state_event_display`        | `true`               | Whether to render state events (e.g. room membership changes, name changes, topic updates) in room timelines.                        |
| `terminal`                   |                      | Configures how __iamb__ should interact with your terminal. See [Terminal](#terminal) below.                                         |
| `typing_notice_display`      | `true`               | Whether to display the typing notifications bar.                                                                                     |
| `typing_notice_send`         | `true`               | Whether to send notifications to other room members when typing.                                                                     |
| `user_gutter_width`          | `30`                 | How much space to reserve for displaying the message sender in room history.                                                         |
| `users`                      | `{}`                 | Configure how other users get displayed in the client. See [User Display](#user-display).                                            |
| `username_display`           | `"username"`         | Configure what name is shown for senders. Valid values are `"username"` (e.g., `@user:example.org`), `"localpart"` (e.g., `user`), or `"displayname"` (e.g., `User Name`) |

For example, if you wanted to raise the timeout to accommodate a long initial
sync, and show more log messages, you could put the following into your
`config.toml`:

```toml
[settings]
log_level = "debug"
request_timeout = 180
```

### Encryption

The `settings.encryption` subsection allows configuring how encryption information
is displayed in the user interface.

```toml
[settings.encryption]
icon_encrypted = "\U0001F512\uFE0E"
icon_unencrypted = "\U0001F513\uFE0E"
indicator_location = "title|prompt"
```

#### Encryption fields

| Name                 | Default                                         | Description                                                                                        |
| ------------------   | ----------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `icon_encrypted`     | `"[E]"`                                         | The icon or text to show when the room is encrypted.                                               |
| `icon_unencrypted`   | `"[U]"`                                         | The icon or text to show when the room is unencrypted.                                             |
| `icon_unknown`       | `"[?]"`                                         | The icon or text to show when the room's encryption status cannot be determined.                   |
| `indicator`          | `"enabled"`                                     | Under what conditions to show the encryption state. Valid values are `"enabled"` (always show), `"disabled"` (never show), `"only-unencrypted"` and `"only-encrypted"`. |
| `indicator_location` | `"prompt"`                                      | Where to show the encryption indicator. Valid values are `"prompt"` for the message bar, `"title"` for the window title, or `"prompt|title"` for both.                  |

### Image Previews

The `settings.image_preview` subsection allows configuring whether and how __iamb__
will display image previews for uploaded images, stickers, and image reactions.

By default, __iamb__ will try to detect an appropriate way to show previews in
your terminal, but you can set `enabled` to `false` to turn it off:

```toml
[settings.image_preview]
enabled = false
```

There are several different supported ways of showing images:

- `"sixel"`, a method supported by several different terminals (see [arewesixelyet.com])
- `"iterm2"`, a method supported by the [iTerm2] terminal for macOS
- `"kitty"`, a method supported by the [Kitty] terminal (requires at least version 0.28.0)
- `"halfblocks"`, a pixelated representation of the image using colored blocks, and used as a fallback

If a method that works for your terminal can't be autodetected (e.g., when
running on Windows or in a terminal that doesn't provide pixel information),
you can manually specify how image previews are done using the `"protocol"`
field:

```toml
[settings.image_preview]
enabled = true
protocol.type = "halfblocks"
protocol.font_size = [ 11, 26 ]
```

The `"type"` field is one of the three methods from above, and `"font_size"`
can be used to specify the width and height of each character cell in pixels.
(Like specifying the `"type"`, this is only necessary if the size in pixels
can't be detected normally using the standard terminal `ioctl` calls.)

You can control the maximum amount of columns/rows that the images take up in
the scrollback using the `"size"` field:

```toml
[settings.image_preview]
size = { height = 10, width = 66 }
```

If the images are not being rescaled as you expect, you can change the filter
algorithm used during resizing with the `filter` field. Possible values are:

- `"CatmullRom"`
- `"Gaussian"`
- `"Lanczos3"`
- `"Nearest"`
- `"Triangle"` (the default)

### Notifications

The `settings.notifications` section allows enabling notifications for messages
sent to rooms not currently open. For example, to enable desktop notifications,
you can put the following in your configuration:

```toml
[settings.notifications]
enabled = true
```

See [Configuring Room Notifications] for how to adjust the per-room
notification level.

#### Notification fields

| Name           | Default                                         | Description                                                                                        |
| -------------- | ----------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `enabled`      | `false`                                         | Whether to send notifications                                                                      |
| `show_message` | `true`                                          | Whether to include the message body when showing the notification                                  |
| `sound_hint`   | (unset)                                         | Configures a [sound hint] (e.g. `"message-new-instant"`) to play when notifications arrive.        |
| `via`          | `"desktop"`                                     | How to deliver notifications: `"desktop"`, `"bell"`, or a pipe-separated string/array of both (e.g. `"desktop\|bell"`). |

Desktop notifications automatically close when a read receipt is sent for the
target message. Large message bodies will be truncated as needed to avoid
generating large notifications.

### Mouse Support

Mouse scroll support can be enabled using the `settings.mouse` section:

```toml
[settings.mouse]
enabled = true
```

When enabled, scrolling with the mouse wheel inside a room is handled as
if they were `<C-E>` and `<C-Y>` scroll movements.

### Sorting Lists

The `settings.sort` section allows you to customize how lists of rooms or users are
sorted in the different __iamb__ windows by specifying which values you want to
sort on. Values are provided as an array of fields, with an optional leading `~`
to flip the sort order from ascending to descending.

For example, if you wanted to group users in the `:members` list together by their
ascending server name and descending localparts, you could do:

```toml
[settings.sort]
members = ["server", "~localpart"]
```

### Sort Fields

| Name      | Default                                         | Description                       |
| --------- | --------------------                            | --------------------------------- |
| `rooms`   | `["favorite", "lowpriority", "unread", "name"]` | How to sort the `:rooms` window   |
| `chats`   | (defaults to `rooms` value)                     | How to sort the `:chats` window   |
| `dms`     | (defaults to `rooms` value)                     | How to sort the `:dms` window     |
| `spaces`  | (defaults to `rooms` value)                     | How to sort the `:spaces` window  |
| `members` | `["power", "knock", "~invite", "id"]`           | How to sort the `:members` window |

#### Room Fields

| Name            | Description                                                                                                       |
| --------------- | ----------------------------------------------------------------------------------------------------------------- |
| `"favorite"`    | Sort rooms with the "Favorite" tag towards the top.                                                               |
| `"invite"`      | Sort pending room invitations towards the top.                                                                    |
| `"lowpriority"` | Sort rooms with the "Low Priority" tag towards the bottom.                                                        |
| `"recent"`      | Sort rooms with recent messages towards the top.                                                                  |
| `"unread"`      | Sort rooms with unread messages towards the top.                                                                  |
| `"name"`        | Sort rooms alphabetically by their room name.                                                                     |
| `"alias"`       | Sort rooms alphabetically by their canonical alias (e.g., `#iamb-users:0x.badd.cafe`)                             |
| `"id"`          | Sort rooms alphabetically by their unique room identifier (e.g., `!nQTgloqKBScxNjsQzR:0x.badd.cafe`).             |
| `"server"`      | Sort rooms alphabetically by the server in their room alias, falling back to the room identifier if there isn't one. |

#### User Fields

| Name            | Description                                                                                                       |
| --------------- | ----------------------------------------------------------------------------------------------------------------- |
| `"power"`       | Sort users by decreasing power level.                                                                             |
| `"id"`          | Sort users alphabetically by their username (e.g. `@user:example.com`)                                            |
| `"invite"`      | Sort users who have been invited to join the room but aren't actually a member yet towards the top.               |
| `"knock"`       | Sort users who have requested to join the room but aren't actually a member yet towards the top.                  |
| `"localpart"`   | Sort users alphabetically by the localpart of their username (e.g. the `@user` portion of `@user:example.com`     |
| `"server"`      | Sort users alphabetically by the server in their username (e.g. the `example.com` portion of `@user:example.com`) |

### Proxying

The `settings.proxy` subsection allows configuring __iamb__ to use a SOCKS5 or HTTPS proxy.
For example, you can run an SSH command like the following to set up a local SOCKS listener:

```shell
ssh -qCND 9050 user@example.com
```

And then use it in your configuration with:

```toml
[settings.proxy]
url = "socks5://localhost:9050
```

Alternatively, if you don't want it to be a permanent part of your configuration, you can use
the usual `ALL_PROXY`, `HTTPS_PROXY`, or `HTTP_PROXY` environment variables to tell __iamb__
to use those:

```shell
ALL_PROXY="socks5://localhost:9050" iamb
```

#### Proxying Fields

| Name                  | Default                                         | Description                                                                                        |
| ------------------    | ----------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `url`                 | (unset)                                         | What URL to proxy requests through.                                                                |
| `auth`                | (unset)                                         | When using an HTTPS proxy, the value to send in the `Proxy-Authorization` header.                  |
| `headers`             | (unset)                                         | When using an HTTPS proxy, this subsection allows specifying additional HTTP headers to include.   |

### Terminal

Terminal-related settings can be configured with the `settings.terminal` subsection.

```toml
[settings.terminal]
cursor_shape = "block"
enable_extended_keys = true
enable_title = false
```

#### Terminal Fields

| Name                  | Default                                         | Description                                                                                        |
| ------------------    | ----------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `cursor_shape`        | `"auto"`                                        | What shape to set the terminal cursor to. Valid values are `"auto"`, `"default"`, `"block"`, `"line"`, and `"underline"`.
| `enable_extended_keys`| `true`                                          | Whether to try to enable extended keypresses if support is detected for the terminal.              |
| `enable_title`        | `true`                                          | Whether to set the terminal window title to `iamb (<user id>)` at startup.                         |

## Startup Layout

You can configure what windows get shown when __iamb__ starts by adding a
`layout` section.

### Restore Previous Layout

By default, the client will try to restore all of the tabs and windows from the
last time it was run. You can explicitly configure this behaviour with:

```toml
[layout]
style = "restore"
```

### New Window

If you want to see a single new window each time you start up, you can set:

```toml
[layout]
style = "new"
```

This will show the `:welcome` window by default, but you can set
`"default_room"` to change it to something else.

### Configured Layout

If you want to start up with the same layout every time regardless of the state
at last exit, you can specify an array of tabs and the window tree in each one:

```toml
[layout]
style = "config"

[[layout.tabs]]
split = [
    { window = "#room1:example.org" },
    { window = "#room2:example.org" }
]

[[layout.tabs]]
split = [
    { split = [ { window = "#room3:example.org" }, { window = "#room4:example.org" } ] },
    { window = "@user:example.org" }
]
```

## Custom Command Aliases

You can map custom aliases to other commands for use in the command bar using
the `aliases` section. For example, if you wanted single-letter variants for
some of the more common commands:

```toml
[aliases]
"c" = "chats"
"d" = "download"
"e" = "edit"
"o" = "open"
"r" = "rooms"
```

## Custom Keybindings

You can add custom keybindings in `macros` subsections, which describes the Vim
modes to map the commands to, the input keys you want to map, and the keys that
you want it to then run. These keybindings behave like macros when a count is
given, and will repeat the target key sequence *n* times.

For example, you could use the following to map `jj` to `<Esc>` in Insert mode
and `V` to `<C-W>m` in Normal and Visual mode:

```toml
[macros.insert]
"jj" = "<Esc>"

[macros."normal|visual"]
"V" = "<C-W>m"
```

You can also use this to trigger commands. For example, to list all chats
when you press 'gc' in normal mode use:

```toml
[macros.normal]
"gc" = ":chats<Enter>"
```

The available modes are:

- `normal`/`n` for Normal mode
- `insert`/`i` for Insert mode
- `visual`/`v` for Visual mode
- `command`/`c` for Command mode
- `select` for Select mode
- `operator-pending` for Operator Pending mode

Use `|` to specify that something should be mapped in several modes.

> If you are unsure how to represent a key, you can you record a macro that use
> it and then look at its representation in the register. For example, you could
> do the following to find the value of the left arrow key:
>
> - Type `qa` to start recording to the `a` register
> - Press the left arrow key
> - Press `q` to stop recording
> - Type `"ap` to paste the contents of the `a` register, yielding `<Left>`

## Directories

__iamb__ will use the standard directories for your operating system, but you
can override them by placing a `"dirs"` field in your `config.toml` containing
any of the following fields. Paths specified in `"dirs"` support expansion of
`~` and shell environment variables (e.g. `$HOME` or `${VAR}`):

| Name                    | Default                            | Description                                                             |
| ----------------------- | ---------------------------------- | ----------------------------------------------------------------------- |
| `cache`                 | [`${dirs::cache_dir}`]`/iamb`           | Directory for __iamb__ data and output that can be safely deleted.      |
| `data`                  | [`${dirs::data_dir}`]`/iamb`            | Directory for __iamb__ data persisted between sessions, like E2EE keys. |
| `downloads`             | [`${dirs::download_dir}`]               | Output directory for downloaded attachments.                            |
| `image_previews`        | `${cache}/image_preview_downloads` | Output directory for caching image displayed when using `image_preview` |
| `logs`                  | `${cache}/logs`                    | Output directory for __iamb__ logs.                                     |

## User Display

You can override how individual users get displayed in the scrollback using the
`settings.users` section.

| Name                    | Default              | Description                                                        |
| ----------------------- | -------------------- | ------------------------------------------------------------------ |
| `color`                 | Determined per-user  | The color to use when showing this user on the screen.             |
| `name`                  | Determined per-user  | The name to use when showing this user on the screen.              |

Valid values for the `color` field are:

- `"black"`
- `"blue"`
- `"cyan"`
- `"dark-gray"`
- `"gray"`
- `"green"`
- `"light-blue"`
- `"light-cyan"`
- `"light-green"`
- `"light-magenta"`
- `"light-red"`
- `"light-yellow"`
- `"magenta"`
- `"none"`
- `"red"`
- `"white"`
- `"yellow"`

For example, if you wanted to override how a bot in a room gets displayed:

```toml
[settings.users]
"@jenkins:example.com" = { name = "jenkins (CI BOT)", color = "light-red" }
```

<style>
table {
    width: 100%;
}
table th:first-of-type {
    width: 30%;
}
table th:nth-of-type(2) {
    width: 30%;
}
table th:nth-of-type(3) {
    width: 40%;
}
</style>

[arewesixelyet.com]: https://www.arewesixelyet.com/
[config.example.toml]: https://github.com/ulyssa/iamb/blob/v0.0.11/config.example.toml
[`${dirs::cache_dir}`]: https://docs.rs/dirs/latest/dirs/fn.cache_dir.html
[dirs::config_dir]: https://docs.rs/dirs/latest/dirs/fn.config_dir.html
[`${dirs::data_dir}`]: https://docs.rs/dirs/latest/dirs/fn.data_dir.html
[`${dirs::download_dir}`]: https://docs.rs/dirs/latest/dirs/fn.download_dir.html
[Configuring Room Notifications]: ./rooms/management.md#configuring-room-notifications
[iTerm2]: https://iterm2.com/
[Kitty]: https://sw.kovidgoyal.net/kitty/
[sound hint]: https://specifications.freedesktop.org/sound-naming/0.2/#notification
[well_known_entry]: https://spec.matrix.org/latest/client-server-api/#getwell-knownmatrixclient
