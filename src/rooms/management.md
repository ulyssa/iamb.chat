# Management

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
- `:invite reject` to rejept the invitation

## Setting Room Properties

You can set the description of the currently focused room using the `:set` command:

```
:room topic set "This is the new room topic"
```

Similarly, if you need to change the room's name:

```
:room name set "Watercooler Discussion"
```

If you want to remove the topic or name, you can use `:room topic unset` or
`:room name unset`.

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
