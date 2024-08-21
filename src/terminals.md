# Terminal Comparisons

While you should be able to use __iamb__ in any terminal with reasonable UTF-8
support, if you want to be able to see images in room history or use keypresses
like `<S-Enter>`, you might find this table useful:

| Terminal          | Operating Systems                               | Images                     | Extended Keypresses     |
| ----------------- | ----------------------------------------------- | -------------------------- | -------------------     |
| [alacritty]       | FreeBSD, Linux, macOS, NetBSD, OpenBSD, Windows | N                          | Y[^note-kitty-keys]     |
| [ConEmu]          | Windows                                         | N[^note-conemu]            | Y[^note-win-keys]       |
| [foot]            | FreeBSD, Linux, OpenBSD                         | Y[^note-sixel]             | Y[^note-kitty-keys]     |
| [gnome-terminal]  | FreeBSD, Linux, NetBSD, OpenBSD                 | N                          | N[^note-gnome-term]     |
| [iTerm2]          | macOS                                           | Y[^note-iterm2-img]        | N                       |
| [kitty]           | FreeBSD, Linux, macOS, NetBSD, OpenBSD          | Y[^note-kitty-img-new]     | Y[^note-kitty-keys]     |
| [konsole]         | FreeBSD, Linux, NetBSD, OpenBSD                 | Y[^note-sixel]             | N[^note-konsole]        |
| [mlterm]          | FreeBSD, Linux, NetBSD, OpenBSD                 | Y[^note-sixel]             | N                       |
| [rio]             | FreeBSD, Linux, macOS, Windows                  | Y[^note-iterm2-img]        | Y[^note-kitty-keys]     |
| [wezterm]         | FreeBSD, Linux, macOS, Windows                  | Y[^note-iterm2-img]        | Y[^note-kitty-keys]     |
| [Windows Terminal]| Windows                                         | Y[^note-sixel]             | Y[^note-win-keys]       |

[^note-kitty-keys]: Uses Kitty enhanced keyboard protocol

[^note-conemu]: See [ConEmu tracking issue](https://github.com/Maximus5/ConEmu/issues/807)

[^note-win-keys]: Uses Windows APIs

[^note-sixel]: Uses [sixel] image protocol

[^note-gnome-term]: See [vte tracking issue](https://gitlab.gnome.org/GNOME/vte/-/issues/2601)

[^note-iterm2-img]: Uses iTerm2 inlines images protocol

[^note-kitty-img-new]: Uses the [new Kitty image protocol](https://sw.kovidgoyal.net/kitty/graphics-protocol/#unicode-placeholders)

[^note-konsole]: See [konsole tracking issue](https://bugs.kde.org/show_bug.cgi?id=435975)

[alacritty]: https://alacritty.org/
[ConEmu]: https://conemu.github.io/
[foot]: https://codeberg.org/dnkl/foot
[gnome-terminal]: https://help.gnome.org/users/gnome-terminal/stable/
[iTerm2]: https://iterm2.com/
[kitty]: https://sw.kovidgoyal.net/kitty/
[konsole]: https://konsole.kde.org/
[mlterm]: https://mlterm.sourceforge.net/
[rio]: https://raphamorim.io/rio/
[sixel]: https://www.arewesixelyet.com/
[wezterm]: https://wezfurlong.org/wezterm/index.html
[Windows Terminal]: https://apps.microsoft.com/detail/9n0dx20hk701
