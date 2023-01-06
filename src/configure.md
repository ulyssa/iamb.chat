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

| Name                    | Default              | Description                                                      |
| ----------------------- | -------------------- | ---------------------------------------------------------------- | 
| `typing_notice`         | `true`               | Whether to send notifications to other room members when typing. |
| `typing_notice_display` | `true`               | Whether to diplay the typing notifications bar.                  |

## Directories

__iamb__ will use the standard directories for your operating system, but you
can override them by placing a `"dirs"` field in your `config.json` containing
any of the following fields:

| Name                    | Default              | Description                                                        |
| ----------------------- | -------------------- | ------------------------------------------------------------------ |
| `cache`                 | [dirs::cache_dir]    | Directory for __iamb__ data and output that can be safely deleted. |
| `logs`                  | `${cache}/logs`      | Output directory for __iamb__ logs.                                |
| `downloads`             | [dirs::download_dir] | Output directory for downloaded attachments.                       |

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
