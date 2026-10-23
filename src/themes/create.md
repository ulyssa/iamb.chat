# Creating Themes

## Overview

Themes can be defined either in your `config.toml` file, which will apply overrides
to whatever values came from the current `settings.theme` value, or you can define
them in their own TOML file in your `themes/` directory, which will allow for easier
switching between different themes.

Everything related to a theme goes in a top-level `[theme]` section:

```toml
[theme]
default.color = "red"
```

The subsections within `[theme]` then allow you to override the colors used for the
relevant parts of the user interface.  Individual, stylable UI elements all have the
following properties:

- `color`, which configures the foreground color for text. This can be one of:
  - An ANSI color name: `"black"`, `"blue"`, `"cyan"`, `"dark-gray"`, `"gray"`,
    `"green"`, `"light-blue"`, `"light-cyan"`, `"light-green"`, `"light-magenta"`,
     `"light-red"`, `"light-yellow"`, `"magenta"`, `"red"`, `"reset"`, `"white"`,
     and `"yellow"`.
  - An indexed color to specify an offset in the 256-color range, e.g. `"57"`
    for a shade of purple, or `"232"` to `"255"` for the greyscale colors.
  - A 24-bit True Color hexadecimal color code, such as `"#000000"` for black
    or `"#ffffff"` for white.
- `background`, which configures the background color for the UI element.
- `modifiers`, which is an array of strings specifying modifiers to how the
  text is styled. Possible values are `"bold"`, `"crossed-out"`, `"dim"`,
  `"hidden"`, `"italic"`, `"rapid-blink"`, `"reversed"`, `"slow-blink"`, and
  `"underlined"`.  Modifier names prefixed with `~` will remove the modifier if
  it was inherited from another default, global config, etc.

Some special UI elements have additional properties:

- `line`, for UI elements that draw a block, such as `theme.windows.border`,
  `theme.messages.code_block`, and `theme.messages.table`. You can specify what
  characters should be used to draw the bounding line using the following values:
  Possible values are `"plain"`, `"rounded"`, `"double"`, `"thick"`,
  `"double-dashed-light"`, `"double-dashed-heavy"`, `"triple-dashed-light"`,
  `"triple-dashed-heavy"`, `"quadruple-dashed-light"`, and `"quadruple-dashed-heavy"`.
- `colors`, for UI elements that can use multiple colors, like `theme.users`
  for usernames. You can specify an array of colors that make up the pallete
  to pick from, or you can set it to `"rainbow-light"` or `"rainbow-dark"` to
  get a large palette of light or dark colors.

## `theme`

The top-level `theme` section contains several special subsections worth noting:

- `default`: the base, default style that everything else should inherit.
- `selected`: how to style selected items in lists and timelines.
- `users`: for controlling how usernames and identifiers are styled.

## `cmdbar`

The `theme.cmdbar` subsections allows controlling how the text in the command bar is styled.
It contains the following stylable subsections:

- `default`, for configure the default styling for the command bar.
- `prompt`, for configuring how the prompt in the command bar is displayed.
- `completions`, for configuring how possible command bar completions are displayed.
- `error`, for configuring how error messages shown in the command bar are displayed.
- `info`, for configuring how information messages shown in the command bar are displayed.

## `completion`

The `theme.completion` subsection allows controlling how the completion menu is styled.
It contains the following stylable subsections:

- `default`, for configuring the default style for entries in the menu.
- `selected`, for configuring how the selected entry is styled.

## `encryption`

The `theme.encryption` subsections allow controlling how the encryption status indicators are styled.
It contains the following stylable subsections:

- `default`, for configuring the default styling for the encryption status indicators.
- `icon_encrypted`, for configuring how the encrypted indicator is styled.
- `icon_unencrypted`, for configuring how the unencrypted indicator is styled.
- `icon_unknown`, for configuring how the unknown encryption status indicator is styled.

## `msgbar`

The `theme.msgbar` subsection allows controlling how the text in the message bar is styled.  
It contains the following stylable subsections:

- `default`, for configuring the default style for the message bar.

## `messages`

The `theme.messages` subsection allows controlling how the bodies of messages are styled.
It contains the following stylable subsections:

- `default`, for configuring the default styling for messages.
- `blockquote`, for configuring how the line used for indenting `<blockquote>` elements in formatted message bodies is styled.
- `code`, for configuring how `<code>` elements in formatted message bodies are displayed.
- `code_block`, for configuring how `<pre>` elements in formatted message bodies are displayed.
- `emphasis`, for configuring how `<em>` and `<i>` elements in formatted message bodies are displayed.
- `ruler`, for configuring the line used for drawing `<ruler>` elements in formatted message bodies.
- `strikethrough`, for configuring how `<del>`, `<s>`, and `<strike>` elements in formatted message bodies are displayed.
- `strong`, for configuring how `<strong>` and `<b>` elements in formatted message bodies are displayed.
- `table`, for configuring the line used for drawing the cells for `<table>` elements in formatted message bodies.
- `underlined`, for configuring how `<u>` elements in formatted message bodies are displayed.

## `timeline`

The `theme.timeline` subsection allows controlling how other elements within the timeline are styled.
It contains the following stylable subsections:

- `default`, for configure the default styling for text in the timeline.
- `date`, for configuring how the dates for messages are styled.
- `time`, for configuring how the time a message was sent is styled.
- `unread_marker`, for configuring line that marks the start of unread messages.
- `state`, for configuring how the text shown for state events is styled.
- `sticker`, for configuring how any text shown for stickers is styled.
- `poll`, for configuring how the text in polls is styled.
- `notice`, for configuring how server notices is styled.
- `redacted`, for configuring how redacted events in the timeline is styled.

## `tabs`

The `theme.tabs` subsection allows controlling how tabs are styled.
It contains the following stylable subsections:

- `title`, for configuring how tab titles are styled.
- `title_focused`, for configuring how the title of the focused tab is styled.

## `windows`

The `theme.windows` subsections allows controlling how the windows are styled.
It contains the following stylable subsections:

- `default`, for configuring the default style for characters that draw the window border or title.
- `border`, for configuring how the border line is styled.
- `border_focused`, for configuring how the border line for the focused window are styled.
- `title`, for configuring how the window titles are styled.

## `rooms`

The `theme.rooms` section allows you to control how lists of rooms like `:unreads`
or `:chats` are styled, and contains several additional subsections that you can
set the core styling properties on:

- `default`, for configuring the default style for text in room lists.
- `labels`, for configuring the style for the labels following room names in lists.
- `notification`, which configures how rooms with unread notifications are
  displayed. This contains the same subsections as `unread`.
- `unread`, for configuring how rooms with unread muted messages are
  displayed. This then contains the following stylable subsections:
  - `number`, for configuring the style of the number showing how many unread notifications a room has.
  - `name`, for configuring the style for room names with unread notifications.
  - `labels`  Configure the style for the labels of rooms with unread notifications.
- `mention`, for configuring how rooms with unread mentions are displayed.
  This contains the same subsections as `unread`.
- `marked_unread`, for configuring how rooms that are manually marked as unread
  are displayed. This contains the same subsections as `unread`.
