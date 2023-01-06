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

- `^Wh` will move to the window left of the current one 
- `^Wj` will move to the window below the current one 
- `^Wk` will move to the window above the current one 
- `^Wl` will move to the window right of the current one 

You can provide a count to the above keybindings to move across multiple windows.

## Organizing Windows

You can reposition open windows using the following keybindings:

- `^WH` will move the current window to the left side of the screen, and use
  the full screen height
- `^WJ` will move the current window to the bottom of the screen, and use the
  full screen width
- `^WK` will move the current window to the top of the screen, and use the full
  screen width
- `^WL` will move the current window to the right side of the screen, and use
  the full screen height

## Closing Windows

You can close a window using `^Wq`, or close all windows but the current one
using `^Wo`. When provided with a count, these keybindings will operate against
that window position instead of the currently focused one.

> If you prefer using commands, you can use `:quit` to close the current
> window, or `:only` to close all windows but the current one.
