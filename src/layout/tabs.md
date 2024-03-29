# Tab Management

## Opening Tabs

You can use the `:tab` command to modify a command that switches the window
content or opens a new window to instead open a new tab. For example:

```
:tab rooms
```

The above command will open the list of joined rooms in a new tab. Similarly,
if you already know what room you want to open:

```
:tab join #watercooler:example.com
```

The above command is equivalent to running:

```
:tabedit #watercooler:example.com`
```

You can also press `<C-W>f` while navigating a list of rooms and users to open it
in a new tab instead.

## Switching Tabs

You can move forwards or backwards through the open tabs using `gt` or `gT`
respectively. If you know want to go to a specific tab, you can prefix `gt`
with the tab number you want to focus on. 

> If you prefer using commands, you can use `:tabn` and `:tabp` to move between
> tabs instead of the keybindings.
>
> You can also move to the first or last tab using `:tabfirst` and `:tablast`.

## Organizing Tabs

You can rearrange your tabs using the `:tabmove` command, like you would in Vim:

- `:tabmove` with no arguments moves the current tab to the end of the tab list
- `:0tabmove` will move the current tab to the beginning of the tab list
- `:-tabmove` will move the current tab left in the tab list
- `:+tabmove` will move the current tab right in the tab list

## Closing Tabs

You can close a tab using `:tabclose`. This will close the current tab with no
arguments, but you can specify a position to close:

- `:tabclose 3` will close the third tab
- `:tabclose $` will close the last tab

If you want to close all tabs but the current one, use `:tabonly`.
