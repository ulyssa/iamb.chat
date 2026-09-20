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

You can see a list of rooms you have been invited to using `:invites`.

## Room Knocking

Room knocking is the reverse of room invitations: a user who is not yet a
member of a room but wants to join it can send a room knock to let someone
inside the room choose whether to invite them in.

You can send a knock through the `:knock send` command:

```
:knock send #room:example.com
```

If you are inside a room and someone has sent a knock request, you can
choose how to handle it:

- `:knock accept @user:example.com` to invite the knocking user to join the room.
- `:knock reject @user:example.com` to reject the room knock from a user.
- `:knock ban @user:example.com` to reject the room knock from a user and prevent them from knocking again.

Knocks will appear in the room's timeline, but you can also look at the
`:members` window for the room to see who has sent a knock.

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

## Upgraded Rooms

When a Matrix room is created, it declared which room version it is using from
the Matrix protocol, which determines the set of features usable within the room
by clients. (See [Feature Matrix], for example.) In order to leverage newer features,
room administrators will "upgrade" the room by creating a successor room that uses
a newer room version, and updating the old room's state to point at the new room.

When this happens, __iamb__ will show you a message and let you know that you can
join the new room by running:

```
:follow next
```

Alternatively, if you are in the upgraded version of a room and want to go to
the older one to read through older discussions, you can do:

```
:follow prev
```

To see what version a room is using, you can run:

```
:room version show
```

If you are a room administrator and you want to make a new room, then you can run:

```
:room version upgrade [VERSION]
```

Starting with room version 12, Matrix supports declaring additional room members
who should also be considered creators of the room, which effectively grants them
an infinite power level. You can specify this when upgrading with:

```
:room version upgrade 12 ++creator=@user:example.com
```

[enabled notifications]: ../configure.md#notifications
[Feautre Matrix]: https://spec.matrix.org/v1.19/rooms/#feature-matrix
