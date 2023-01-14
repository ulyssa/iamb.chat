# Messages

## Sending

While the message bar of a room is selected, you can type a message that you
wish to send. When it's complete, you can send it by pressing the `<Enter>`
key from either Normal or Insert mode.

> If you need to type a multiline message, you can start a line by typing
> `^V^J`.  You can also use the `O` and `o` keys to insert a blank line before
> or after the current line respectively.

The `:upload` command allows you to specify a file to send to the currently
focused room:

```
:upload "/home/user/Documents/Shared Document.pdf"
```

## Message Scrollback

You can scroll through messages from the message bar using the following keys:

- `^E`/`^Y` to scroll downwards and upwards respectively a line at a time
- `^D`/`^U` to scroll downwards and upwards respectively by half the window height
- `^F`/`^B` to scroll downwards and upwards respectively by the window height

If you want to use movement keys to select individual messages, you can toggle
focus between the message bar and the scrollback by pressing `^Wm`.

## Replying To A Message

If you select a message in the scrollback, you can reply to it using the
`:reply` command. This will refocus the message bar, where you can type out
your reply. You can then [send it](#sending) the same way that you would a
normal message.

If you change your mind, or select the wrong message to reply to, you can use
`:cancel` to undo your `:reply`.

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
