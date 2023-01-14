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
:set room.topic "This is the new room topic"
```

Similarly, if you need to change the room's name:

```
:set room.topic "Watercooler Discussion"
```
