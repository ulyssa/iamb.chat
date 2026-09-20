# Browsing

## Browsing Rooms

You can switch to a list of joined rooms using the `:rooms` command.

## Browsing Direct Messages

You can switch to a list of direct messages using the `:dms` command.

## Browsing Rooms And DMs Together

You can switch to a list of both joined rooms and direct messages using the
`:chats` command.

## Browsing Unreads

You can view a list of rooms and direct messages with unread messages
using the `:unreads` command. If you don't want to visit all of them
to read them each individually, you can mark them all as read with:

```
:unreads clear
``` 

If you just want to see a list of rooms that have unread mentions
instead of every room with unread conversation, then you can use:

```
:mentions
```

If you read a room, but then want to expicitly mark it unread to
come back to later, you can run:

```
:room unread set
```

Or to remote the explicit unread marker:

```
:room unread unset
```

## Browsing Spaces

You can switch to a list of joined spaces using the `:spaces` command.
Use `/` and `?` to search by space name or room ID within the list.
