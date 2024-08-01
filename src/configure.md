# Configuration

__iamb__ is configurable via a TOML configuration file located in the
configuration directory. By default, the configuration directory is determined
by [dirs::config_dir], but you can override it at startup with the `-C`
command-line flag.

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

### Per-Profile Configuration

Several of the sections that you can place under the global configuration can
also be placed within profile configurations to achieve per-profile values:

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
| `default_room`               |                      | A default room name or username to open at startup, in place of showing the welcome screen.                                          |
| `image_preview`              | (unset)              | Configures displaying image attachments for terminals that support previewing images. See [Image Previews](#image-previews) below.   |
| `log_level`                  | `"info"`             | Configures the minimum log level. Valid values are `"trace"`, `"debug"`, `"info"`, `"warn"` or `"error"`.                            |
| `message_user_color`         | `false`              | Whether to color entire messages using the same color used for the sender's username and display name.                               |
| `message_shortcode_display`  | `false`              | Whether to replace Emojis in message bodies with their shortcodes.                                                                   |
| `notifications`              | (unset)              | Whether to generate desktop notifications for messages sent to rooms not currently being viewed. See [Notifications](#notifications) |
| `open_command`               |                      | Configures a command to use for opening downloads instead of the default. (e.g., `["my-open", "--file"]` to run a custom script      |
| `reaction_display`           | `true`               | Whether to display message reactions. You can use this or `reaction_shortcode_display` if your terminal doesn't show Emojis well.    |
| `reaction_shortcode_display` | `false`              | Whether to show the shortcode value instead of the Emoji for reactions. If no shortcode is available, then it won't be displayed.    |
| `read_receipt_display`       | `true`               | Whether to display read receipts next to messages in the room scrollback.                                                            |
| `read_receipt_send`          | `true`               | Whether to send read receipts for viewed rooms.                                                                                      |
| `request_timeout`            | 120                  | How long to wait in seconds before timing out requests to the homeserver.                                                            |
| `sort`                       |                      | Configures how to sort the lists in different windows like `:rooms` or `:members`. See [Sorting Lists](#sorting-lists) below.        |
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

### Image Previews

When the `settings.image_preview` subsection is present, __iamb__ will
try to detect an appropriate way to show previews of image attachments:

```toml
[settings]
image_preview = {}
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

### Notifications

The `settings.notifications` section allows enabling notifications for messages
sent to rooms not currently open. For example, to enable desktop notifications,
you can put the following in your configuration:

```toml
[settings.notifications]
enabled = true
```

#### Notification fields

| Name           | Default                                         | Description                                                                                        |
| -------------- | ----------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `enabled`      | `false`                                         | Whether to send notifications                                                                      |
| `show_message` | `true`                                          | Whether to include the message body when showing the notification                                  |
| `via`          | `"desktop"`                                     | How to deliver the notification: `"desktop"` for desktop mechanism, or `"bell"` for terminal bell. |


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
| `members` | `["power", "id"]`                               | How to sort the `:members` window |

#### Room Fields

| Name            | Description                                                                                                       |
| --------------- | ----------------------------------------------------------------------------------------------------------------- |
| `"favorite"`    | Sort rooms with the "Favorite" tag towards the top.                                                               |
| `"lowpriority"` | Sort rooms with the "Low Priority" tag towards the bottom.                                                        |
| `"recent"`      | Sort rooms with recent messages towards the top.                                                                  |
| `"unread"`      | Sort rooms with unread messages towards the top.                                                                  |
| `"name"`        | Sort rooms alphabetically by their room name.                                                                     |
| `"alias"`       | Sort rooms alphabetically by their canonical alias (e.g., `#iamb-users:0x.badd.cafe`)                              |
| `"id"`          | Sort rooms alphabetically by their unique room identifier (e.g., `!nQTgloqKBScxNjsQzR:0x.badd.cafe`).             |

#### User Fields 

| Name            | Description                                                                                                       |
| --------------- | ----------------------------------------------------------------------------------------------------------------- |
| `"power"`       | Sort users by decreasing power level.                                                                             |
| `"id"`          | Sort users alphabetically by their username (e.g. `@user:example.com`)                                            |
| `"localpart"`   | Sort users alphabetically by the localpart of their username (e.g. the `@user` portion of `@user:example.com`     |
| `"server"`      | Sort users alphabetically by the server in their username (e.g. the `example.com` portion of `@user:example.com`) |

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
any of the following fields:

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
[`${dirs::cache_dir}`]: https://docs.rs/dirs/latest/dirs/fn.cache_dir.html
[dirs::config_dir]: https://docs.rs/dirs/latest/dirs/fn.config_dir.html
[`${dirs::data_dir}`]: https://docs.rs/dirs/latest/dirs/fn.data_dir.html
[`${dirs::download_dir}`]: https://docs.rs/dirs/latest/dirs/fn.download_dir.html
[iTerm2]: https://iterm2.com/
[Kitty]: https://sw.kovidgoyal.net/kitty/
[well_known_entry]: https://spec.matrix.org/latest/client-server-api/#getwell-knownmatrixclient
