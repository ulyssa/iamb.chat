# Configuration

__iamb__ is configurable via a JSON configuration file located in the
configuration directory. By default, the configuration directory is determined
by [dirs::config_dir], but you can override it at startup with the `-C`
command-line flag.

## Profiles

You can configure a Matrix account in your `config.json` by adding a new field
to the `"profiles"` object. For example, if you had two different accounts on
your homeserver:

```json
{
    "profiles": {
        "admin": {
            "user_id": "@user1:example.com",
            "url": "https://example.com"
        },
        "user": {
            "user_id": "@user2:example.com",
            "url": "https://example.com"
        }
    },
    "default_profile": "user"
}
```

With the `"default_profile"` field set, __iamb__ will default to using the
`user` profile at startup. You can manually specify what you want via the `-P`
flag. For example:

```
$ iamb -P admin
Logging in for @user1:example.com...
```

## Settings

| Name                         | Default              | Description                                                                                                                       |
| ---------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `default_room`               |                      | A default room name or username to open at startup, in place of showing the welcome screen.                                       |
| `log_level`                  | `"info"`             | Configures the minimum log level. Valid values are `"trace"`, `"debug"`, `"info"`, `"warn"` or `"error"`.                         |
| `open_command`               |                      | Configures a command to use for opening downloads instead of the default. (e.g., `["my-open", "--file"]` to run a custom script   |
| `request_timeout`            | 120                  | How long to wait in seconds before timing out requests to the homeserver.                                                         |
| `reaction_display`           | `true`               | Whether to display message reactions. You can use this or `reaction_shortcode_display` if your terminal doesn't show Emojis well. |
| `reaction_shortcode_display` | `false`              | Whether to show the shortcode value instead of the Emoji for reactions. If no shortcode is available, then it won't be displayed. |
| `read_receipt_send`          | `true`               | Whether to send read receipts for viewed rooms.                                                                                   |
| `read_receipt_display`       | `true`               | Whether to display read receipts next to messages in the room scrollback.                                                          |
| `typing_notice_send`         | `true`               | Whether to send notifications to other room members when typing.                                                                  |
| `typing_notice_display`      | `true`               | Whether to display the typing notifications bar.                                                                                   |
| `users`                      | `{}`                 | Configure how other users get displayed in the client. See [User Display](#user-display).                                         |
| `username_display`           | `"username"`         | Configure what name is shown for senders. Valid values are `"username"` (e.g., `@user:example.org`), `"localpart"` (e.g., `user`), or `"displayname"` (e.g., `User Name`) |

For example, if you wanted to raise the timeout to accommodate a long initial
sync, and show more log messages, you could put the following into your
`config.json`:

```json
{
    "settings": {
        "log_level": "debug",
        "request_timeout": 180
    }
}
```

## Startup Layout

You can configure what windows get shown when __iamb__ starts by adding a
`"layout"` object.

### Restore Previous Layout

By default, the client will try to restore all of the tabs and windows from the
last time it was run. You can explicitly configure this behaviour with:

```json
{
    "layout": { "style": "restore" }
}
```

### New Window

If you want to see a single new window each time you start up, you can set:

```json
{
    "layout": { "style": "new" }
}
```

This will show the `:welcome` window by default, but you can set
`"default_room"` to change it to something else.

### Configured Layout

If you want to start up with the same layout every time regardless of the state
at last exit, you can specify an array of tabs and the window tree in each one:

```json
{
    "layout": {
        "style": "config",
        "tabs": [
            {
                "split": [
                    { "window": "#room1:example.org" },
                    { "window": "#room2:example.org" }
                ]
            },
            {
                "split": [
                    {
                        "split": [
                            { "window": "#room3:example.org" },
                            { "window": "#room4:example.org" }
                        ]
                    },
                    { "window": "@user:example.org" }
                ]
            }
        ]
    }
}
```

## Directories

__iamb__ will use the standard directories for your operating system, but you
can override them by placing a `"dirs"` field in your `config.json` containing
any of the following fields:

| Name                    | Default              | Description                                                        |
| ----------------------- | -------------------- | ------------------------------------------------------------------ |
| `cache`                 | [dirs::cache_dir]    | Directory for __iamb__ data and output that can be safely deleted. |
| `logs`                  | `${cache}/logs`      | Output directory for __iamb__ logs.                                |
| `downloads`             | [dirs::download_dir] | Output directory for downloaded attachments.                       |

## User Display

You can override how individual users get displayed in the scrollback using the
`"users"` field of the `"settings"` object.

| Name                    | Default              | Description                                                        |
| ----------------------- | -------------------- | ------------------------------------------------------------------ |
| `color`                 | Determined per-user  | The color to use when showing this user on the screen.             |
| `name`                  | Determined per-user  | The name to use when showing this user on the screen.              |

Valid values for the `"colors"` field are:

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

```json
{
    "settings": {
        "users": {
            "@jenkins:example.com": {
                "name": "jenkins (CI BOT)",
                "color": "light-red"
            }
        }
    }
}
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

[dirs::cache_dir]: https://docs.rs/dirs/latest/dirs/fn.cache_dir.html
[dirs::config_dir]: https://docs.rs/dirs/latest/dirs/fn.config_dir.html
[dirs::download_dir]: https://docs.rs/dirs/latest/dirs/fn.download_dir.html
