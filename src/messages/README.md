# Messages

## Sending

While the message bar of a room is selected, you can type a message that you
wish to send. When it's complete, you can send it by pressing the `<Enter>`
key from either Normal or Insert mode.

> If you need to type a multiline message, you can start a line by typing
> `<C-V><C-J>`. You can also use the `O` and `o` keys to insert a blank line
> before or after the current line respectively.

From within the message bar, you can complete Matrix usernames, room aliases
and identifiers, and Emoji shortcodes (e.g., `:heart:`) by using `<C-N>` and
`<C-P>` to start cycling forwards or backwards through the list of possible
completions.

The `:upload` command allows you to specify a file to send to the currently
focused room:

```
:upload "/home/user/Documents/Shared Document.pdf"
```

Clipboard images can be uploaded by pasting with `p` or `P` from the `"+` and
`"*` registers, and following the confirmation dialog. On macOS and Windows
they contain the same contents, but they differ on Linux and other \*nix
systems running X11 or Wayland, where:

- `"+` contains the CLIPBOARD selection, which is usually set in a GUI
  application with `<C-C>` or by selecting "Copy Image" in a menu dialog.
- `"*` contains the PRIMARY selection, which is usually the last selected text
  in X11 or Wayland.

So, for example, if you had copied an image from a web browser on Linux
(placing it into the CLIPBOARD selection), you could paste it into `iamb` with
`"+p`. Or, if you instead selected some text with your cursor (placing it into
the PRIMARY selection), then you could paste it with `"*p`.

> If you want to compose a longer message outside of __iamb__ in your preferred
> text editor, you can use the `:editor` command to launch your configured
> `$EDITOR`.

## Message Slash Commands

You can prefix a message with several different slash commands to change the
message type or format:

- `/me` to send an emote message
- `/html`/`/h` to send an HTML body
- `/plain`/`/p` to send a plaintext body

These slash commands won't appear with any special effects in __iamb__, but do
produce effects in other clients:

- `/confetti` to add confetti effects
- `/fireworks` to add fireworks effects
- `/hearts` to add floating hearts
- `/snowfall` to add snowfall effects
- `/rainfall` to add rainfall effects
- `/spaceinvaders` to add falling [Space Invaders]

## Message Scrollback

You can scroll through messages from the message bar using the following keys:

- `<C-E>`/`<C-Y>` to scroll downwards and upwards respectively a line at a time
- `<C-D>`/`<C-U>` to scroll downwards and upwards respectively by half the window height
- `<C-F>`/`<C-B>` to scroll downwards and upwards respectively by the window height

If you want to use movement keys to select individual messages, you can toggle
focus between the message bar and the scrollback by pressing `<C-W>m`.

The plaintext content of messages can be copied to registers using yank
keybindings like `yy` or `Y`, and marked with `m{a-z}`. Marked messages can
then be returned to via `'{a-z}`.

You can search the plaintext content of messages using `?` and `/` for reverse
and forward search respectively. The `n` and `N` keys can be used to jump
between results.

## Threads

You can enter or create a thread by selecting the message in the scrollback and
pressing `<Enter>`. This will open a thread view that will show you messages
in that thread. If you send a message in this view, it will be sent in-thread.

Entering the thread view puts an entry into the jumplist, so when you are ready
to return to the main room view, you can use `^O` to move backwards through the
jumplist.

## Replying To A Message

If you select a message in the scrollback, you can reply to it using the
`:reply` command. This will refocus the message bar, where you can type out
your reply. You can then [send it](#sending) the same way that you would a
normal message.

If you change your mind, or select the wrong message to reply to, you can use
`:cancel` to undo your `:reply`.

## Editing Messages

Once a message has been sent, you might find that you need to amend it, to fix
typos or correct information. You can select the message and run the `:edit`
command. This will update the text box to include the message's original body
for you to edit.

Once you've finished correcting the message, you can send it just like other
messages to update the original.

## Reacting To A Message

If you want to react to a message with an Emoji, you can select it in the
scrollback, and then use the `:react` command. For example:

```
:react ❤️
```

As a convenience, you can use the [GitHub Emoji shortcodes] to refer to them
instead. For example, we could have also written the above as:

```
:react heart
```

If the argument isn't the shortcode name of an Emoji, then you will be prompted
for whether you want to react with the literal text. You can force literal text
by adding a `!` to the argument. For example, none of these will appear as Emoji:

```
:react! heart
:react! laughing
:react! "hello world"
```

If you want to remove a reaction, you can do so with the `:unreact` command. By
default, this will remove all your reactions from the specified message, but
you can give a name if you've made any that you want to keep:

```
:unreact heart
```

## Redacting A Message

If you need to remove a message from a room, you can do so using the `:redact`
command on the message. This command optionally takes a single argument giving
the reason for removing it. For example:

```
:redact "Message violates room rules"
```

If you're removing a message because it contains secrets (e.g. passwords,
authentication tokens, etc.), make sure to rotate them: redacting a message
prevents people from seeing it in the future, but users in the room at the time
it was originally sent may have already seen it, and it may still live in the
room logs of some clients or bots.

## Downloading Attachments

If you select an attachment in the scrollback, you can download it using the
`:download` command:

- When given no arguments, __iamb__ will download the attachment to the
  configured `downloads` directory
- When given a directory as an argument, the file will be saved there
- Otherwise, the file file will be saved to the given path

If there is already a file of the same name, __iamb__ will not overwrite it.
You can use `:download!` to replace the file.

To open the file after downloading the file, use the `:open` command instead.

## Opening Links

Links in messages are each assigned a number (or a letter when there are more
than 10 links), which is shown within brackets (like `[0]`). You can use
`:open` to view a list of their matching URLs, and pick one to open in a
browser by typing its assigned character.

[GitHub Emoji shortcodes]: https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md
[open_command]: ./configure.md#Settings
[Space Invaders]: https://en.wikipedia.org/wiki/Space_Invaders
