# Themes

__iamb__ supports re-styling many aspects of the user interface both in your
configuration and with dedicated theme files. You can put them into a `themes`
directory in your configuration directory (e.g., `~/.config/iamb/themes/name.toml`
on Linux systems), and then use it by running either `:theme name` to switch
your theme to it, or by putting in your `config.toml`:

```toml
[settings]
theme = "name"
```

The __iamb__ repository contains [multiple themes][themes] ported from Vim's
colorschemes, which you can download and place in your `~/.config/iamb/themes`.
Alternatively, your installation source may have already packaged them at
`/usr/share/iamb/themes/`, which __iamb__ will search for themes at startup.

See [Creating Themes] and [Theme Gallery] for building or picking a theme.

[themes]: https://github.com/ulyssa/iamb/tree/main/themes
[Creating Themes]: ./create.md
[Theme Gallery]: ./gallery.md
