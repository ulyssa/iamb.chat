# Window Management

## Opening Windows

You can use `:split` (or its vertical variant `:vsplit`) to split the current
window. You can optionally provide a room or user to open that room instead.
For example:

```
:vsplit #alias:example.com
```

Will vertically split the current window and open `#alias:example.com` in the
new window.

> If you only need to duplicate the window without changing its content, you
> can use `<C-W>s` and `<C-W>v` to horizontally and vertically split the
> current window.

By default, the split commands will open the new window so that it is
visually before the current one, but you can alter this using `:belowright`
(as opposed to the default `:aboveleft` behaviour). Similarly, you can also
change the axis of a split using the `:vertical` and `:horizontal` commands.

Several of the commands within __iamb__ change the displayed content in the
current window. You can force them to instead open a new window using the above
commands. For example, to open the list of rooms below the current window:

```
:bel rooms
```

Or, to show a room's members to the left side of the room instead of the right:

```
:abo hor members
```

## Switching Windows

You can switch between between neighboring windows using the following keybindings:

- `<C-W>h` will move to the window left of the current one 
- `<C-W>j` will move to the window below the current one 
- `<C-W>k` will move to the window above the current one 
- `<C-W>l` will move to the window right of the current one 

If you want to move to previous content in the window, you can navigate through
the jumplist using:

- `<C-O>` to move backwards through the jumplist
- `<C-I>` to move forward through the jumplist

You can provide a count to all of the above keybindings to repeat them multiple
times.

## Organizing Windows

You can reposition open windows using the following keybindings:

- `<C-W>H` will move the current window to the left side of the screen, and use
  the full screen height
- `<C-W>J` will move the current window to the bottom of the screen, and use the
  full screen width
- `<C-W>K` will move the current window to the top of the screen, and use the full
  screen width
- `<C-W>L` will move the current window to the right side of the screen, and use
  the full screen height

Sometimes, you may find yourself wanting to make a window occupy
the whole screen without closing any of the other windows. You can:

- Use `<C-W>z` to zoom in and out of a window without changing your current layout
- Use `<C-W>T` to extract the window into its own [tab](./tabs.md)

## Resizing Windows

You can resize windows using the following keybindings:

- `<C-W>-` will decrease the current window height by the specified count
- `<C-W>+` will increase the current window height by the specified count
- `<C-W><` will decrease the current window width by the specified count
- `<C-W>>` will increase the current window width by the specified count
- `<C-W>=` will attempt to resize all windows in the same row or column to have
  equal height and width

> If your window manager or terminal is capturing `<C-W>`, you can use the
> `:resize` command to change window height. For example, `:resize -10` will
> decrease the height by ten, and `:resize +5` will increase it by 5.
>
> To change the window width, use `:vertical resize` instead.

## Closing Windows

You can close a window using `<C-W>q`, or close all windows but the current one
using `<C-W>o`. When provided with a count, these keybindings will operate against
that window position instead of the currently focused one.

> If you prefer using commands, you can use `:quit` to close the current
> window, or `:only` to close all windows but the current one.
