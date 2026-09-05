# Terminal Comparisons

While you should be able to use __iamb__ in any terminal with reasonable UTF-8
support, if you want to be able to see images in room history or use keypresses
like `<S-Enter>`, you might find this table useful:

| Terminal                        | Operating Systems                               | Images                     | Extended Keypresses |
| -----------------               | ----------------------------------------------- | -------------------------- | ------------------- |
| [alacritty][^license-mit]       | FreeBSD, Linux, macOS, NetBSD, OpenBSD, Windows | N                          | Y[^note-kitty-keys] |
| [ConEmu][^license-bsd3]         | Windows                                         | N[^note-conemu]            | Y[^note-win-keys]   |
| [contour][^license-apache]      | FreeBSD, Linux, macOS, OpenBSD, Windows         | Y[^note-sixel]             | N                   |
| [foot][^license-mit]            | FreeBSD, Linux, OpenBSD                         | Y[^note-sixel]             | Y[^note-kitty-keys] |
| [ghostty][^license-mit]         | Linux, macOS                                    | Y[^note-kitty-img-new]     | Y[^note-kitty-keys] |
| [gnome-terminal][^license-gpl3] | FreeBSD, Linux, NetBSD, OpenBSD                 | N                          | N[^note-gnome-term] |
| [iTerm2][^license-gpl2]         | macOS                                           | Y[^note-iterm2-img]        | N                   |
| [kitty][^license-gpl3]          | FreeBSD, Linux, macOS, NetBSD, OpenBSD          | Y[^note-kitty-img-new]     | Y[^note-kitty-keys] |
| [konsole][^license-gpl2]        | FreeBSD, Linux, NetBSD, OpenBSD                 | Y[^note-sixel]             | N[^note-konsole]    |
| [mlterm][^license-bsd3]         | FreeBSD, Linux, NetBSD, OpenBSD                 | Y[^note-sixel]             | N                   |
| [rio][^license-mit]             | FreeBSD, Linux, macOS, Windows                  | Y[^note-iterm2-img]        | Y[^note-kitty-keys] |
| [wezterm][^license-mit]         | FreeBSD, Linux, macOS, Windows                  | Y[^note-iterm2-img]        | Y[^note-kitty-keys] |
| [Windows Terminal][^license-mit]| Windows                                         | Y[^note-sixel]             | Y[^note-win-keys]   |

<style>
table {
    width: 100%;
}
table th:first-of-type {
    width: 25%;
}
table th:nth-of-type(2) {
    width: 35%;
}
table th:nth-of-type(3) {
    width: 20%;
}
table th:nth-of-type(4) {
    width: 20%;
}
</style>

[^note-kitty-keys]: Uses Kitty enhanced keyboard protocol

[^note-conemu]: See [ConEmu tracking issue](https://github.com/Maximus5/ConEmu/issues/807)

[^note-win-keys]: Uses Windows APIs

[^note-sixel]: Uses [sixel] image protocol

[^note-gnome-term]: See [vte tracking issue](https://gitlab.gnome.org/GNOME/vte/-/issues/2601)

[^note-iterm2-img]: Uses iTerm2 inlines images protocol

[^note-kitty-img-new]: Uses the [new Kitty image protocol](https://sw.kovidgoyal.net/kitty/graphics-protocol/#unicode-placeholders)

[^note-konsole]: See [konsole tracking issue](https://bugs.kde.org/show_bug.cgi?id=435975)

[^license-apache]: Open sourced under the Apache 2.0 license
[^license-bsd3]: Open sourced under a BSD 3-Clause license
[^license-gpl2]: Open sourced under the GNU Public License version 2
[^license-gpl3]: Open sourced under the GNU Public License version 3
[^license-mit]: Open sourced under the MIT license


[alacritty]: https://alacritty.org/
[ConEmu]: https://conemu.github.io/
[contour]: https://contour-terminal.org/
[foot]: https://codeberg.org/dnkl/foot
[gnome-terminal]: https://help.gnome.org/users/gnome-terminal/stable/
[ghostty]: https://ghostty.org/
[iTerm2]: https://iterm2.com/
[kitty]: https://sw.kovidgoyal.net/kitty/
[konsole]: https://konsole.kde.org/
[mlterm]: https://mlterm.sourceforge.net/
[rio]: https://raphamorim.io/rio/
[sixel]: https://www.arewesixelyet.com/
[wezterm]: https://wezterm.org/
[Windows Terminal]: https://github.com/microsoft/terminal/
