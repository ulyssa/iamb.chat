# Management

## Room Creation

You can create new rooms and spaces using the `:create` command. By default,
the room is private and unencrypted, but you can use the following flags to
configure how it is initially created:

- `++space` to make it a space
- `++public` to make the room publicly joinable
- `++enc`/`++encrypted` to make it an encrypted room
- `++alias=__localpart__` to set a canonical alias

For example, you could use the following to create a new public space `#community:example.com`:

```
:create ++space ++alias=community ++public
```

## Room Invitations

Private Matrix rooms require someone to be let in by a current member with a
high enough power level. You can invite someone to join a room through the
`:invite send` command:

```
:invite send @user:example.com
```

The user will receive an invitation that they can then choose to accept or
reject. If you've received an invitation to a room, space, or direct message,
you can open it up, focus the window and run:

- `:invite accept` to accept the invitation and join the room
- `:invite reject` to reject the invitation

## Marking Direct Rooms

Matrix keeps a list of direct message rooms in account data on the server. If
you have a room that you want to appear under `:dms` and it's not currently
there, you can add the currently focused room to your account's list of direct
messages with:

```
:room dm set
```

Similarly, if you *don't* want it to be a DM:

```
:room dm unset
```

## Setting Room Tags

Matrix rooms can be tagged to help with sorting them. Several special tags that
Matrix defines are:

- `m.favourite` for favorite rooms that you look at often
- `m.lowpriority` for rooms that you don't look at often
- `m.server_notice` for rooms where homeserver announcements are made

In __iamb__, you can modify the tags of an open room using:

```
:room tag set m.favourite
```

You can use `:room tag set fav` as a shorthand for `m.favourite`, and `:room
tag set low` as a shorthand for `m.lowpriority`.

If you want to unset a tag, you can do:

```
:room tag unset fav
```

Matrix also allows users to apply their own tags that start with `u.`. For
example, if you wanted to mark rooms that are bridged to an IRC channel, you
could do:

```
:room tag set u.irc
```

Note that user tags are not shown by all clients, so while they will appear in
__iamb__, you won't necessarily see them elsewhere.

## Configuring Room Notifications

If you've [enabled notifications], you may want to reconfigure some rooms to
not notify you as much. The different notification levels are:

- `mute`, which disables notifications for this room.
- `keywords`/`mentions`, which only shows notifications for mentions of the user and configured keywords.
- `all`, which shows notifications for every message to this room.

You can update a room with:

```
:room notify set [mute|keywords|mentions|all]
```

You can remove the per-room override with:

```
:room notify unset
```

And see the currently configured value for the room with:

```
:room notify show
```

[enabled notifications]: ../configure.md#notifications
