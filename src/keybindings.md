# Keybinding Reference

## iamb keybindings

| Modes           | Keybinding        | Aliases        | Help                                          |
| --------------- | ----------------- | -------------- | --------------------------------------------- |
| Normal, Visual  | `<C-W>m`          | `<C-W><C-M>`   | See [Message Scrollback]                      |
| Normal, Visual  | `<C-W>z`          | `<C-W><C-Z>`   | See [Organizing Windows]                      |

## Vim keybindings

Note that this is not a complete list of all Vim keybindings available within
__iamb__, but just some of those referenced and explained throughout this
documentation.

| Modes           | Keybinding        | Aliases        | Help                                          |
| -----           | ---------------   | -------------- | --------------------------------------------- |
| Normal, Visual  | `gf`              |                | See [Following Matrix IDs]                    |
| Normal          | `gt`              | `<C-PageDown>` | See [Switching Tabs]                          |
| Normal          | `gT`              | `<C-PageUp>`   | See [Switching Tabs]                          |
| Normal          | `m{a-z}`          |                | See [Message Scrollback]                      |
| Normal          | `n`               |                | See [Message Scrollback]                      |
| Normal          | `N`               |                | See [Message Scrollback]                      |
| Normal          | `o`               |                | See [Sending]                                 |
| Normal          | `O`               |                | See [Sending]                                 |
| Normal          | `yy`              |                | See [Message Scrollback]                      |
| Normal          | `Y`               |                | See [Message Scrollback]                      |
| Normal          | `'{a-z}`          |                | See [Message Scrollback]                      |
| Normal          | `/`               |                | See [Message Scrollback]                      |
| Normal          | `?`               |                | See [Message Scrollback]                      |
| Normal, Visual  | `<C-B>`           | `<PageUp>`     | See [Message Scrollback]                      |
| Normal, Visual  | `<C-E>`           |                | See [Message Scrollback]                      |
| Normal, Visual  | `<C-F>`           | `<PageDown>`   | See [Message Scrollback]                      |
| Normal, Visual  | `<C-D>`           |                | See [Message Scrollback]                      |
| Normal          | `<C-I>`           | `<Tab>`        | See [Switching Windows]                       |
| Normal          | `<C-L>`           |                | Force the window to redraw                    |
| Insert          | `<C-N>`           |                | See [Sending]                                 |
| Normal          | `<C-O>`           |                | See [Switching Windows]                       |
| Insert          | `<C-P>`           |                | See [Sending]                                 |
| Normal, Visual  | `<C-U>`           |                | See [Message Scrollback]                      |
| Normal, Visual  | `<C-W>f`          | `<C-W><C-F>`   | See [Following Matrix IDs]                    |
| Normal, Visual  | `<C-W>gf`         |                | See [Following Matrix IDs] and [Opening Tabs] |
| Normal, Visual  | `<C-W>h`          | `<C-W><C-H>`   | See [Switching Windows]                       |
| Normal, Visual  | `<C-W>H`          |                | See [Organizing Windows]                      |
| Normal, Visual  | `<C-W>j`          | `<C-W><C-J>`   | See [Switching Windows]                       |
| Normal, Visual  | `<C-W>J`          |                | See [Organizing Windows]                      |
| Normal, Visual  | `<C-W>k`          | `<C-W><C-K>`   | See [Switching Windows]                       |
| Normal, Visual  | `<C-W>K`          |                | See [Organizing Windows]                      |
| Normal, Visual  | `<C-W>l`          | `<C-W<C-L>`    | See [Switching Windows]                       |
| Normal, Visual  | `<C-W>L`          |                | See [Organizing Windows]                      |
| Normal, Visual  | `<C-W>o`          | `<C-W><C-O>`   | See [Closing Windows]                         |
| Normal, Visual  | `<C-W>q`          | `<C-W><C-Q>`   | See [Closing Windows]                         |
| Normal, Visual  | `<C-W>s`          | `<C-W><C-S>`   | See [Opening Windows]                         |
| Normal, Visual  | `<C-W>T`          |                | See [Organizing Windows]                      |
| Normal, Visual  | `<C-W>v`          | `<C-W><C-V>`   | See [Opening Windows]                         |
| Normal, Visual  | `<C-W>-`          |                | See [Resizing Windows]                        |
| Normal, Visual  | `<C-W>+`          |                | See [Resizing Windows]                        |
| Normal, Visual  | `<C-W><`          |                | See [Resizing Windows]                        |
| Normal, Visual  | `<C-W>>`          |                | See [Resizing Windows]                        |
| Normal, Visual  | `<C-W>=`          |                | See [Resizing Windows]                        |
| Normal, Visual  | `<C-Y>`           |                | See [Message Scrollback]                      |

<style>
table {
    width: 100%;
}
table th:first-of-type {
    width: 25%;
}
table th:nth-of-type(2) {
    width: 10%;
}
table th:nth-of-type(3) {
    width: 25%;
}
table th:nth-of-type(4) {
    width: 40%;
}
</style>

[Closing Windows]: ./layout/windows.md#closing-windows
[Following Matrix IDs]: ./layout/index.md#following-matrix-ids
[Message Scrollback]: ./messages/#message-scrollback
[Opening Tabs]: ./layout/tabs.md#opening-tabs
[Opening Windows]: ./layout/windows.md#opening-windows
[Organizing Windows]: ./layout/windows.md#organizing-windows
[Resizing Windows]: ./layout/windows.md#resizing-windows
[Sending]: ./messages/#sending
[Switching Tabs]: ./layout/tabs.md#switching-tabs
[Switching Windows]: ./layout/windows.md#switching-windows
