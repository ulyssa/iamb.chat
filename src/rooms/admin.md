# Administration

If you have the appropriate power level in a room, then you can change room
settings and membership as described throughout this page. 

## Managing Room Membership

Both bot spam and aggressive users are an unfortunately reality, and you may
sometimes find yourself needing to get rid of users in a room. You can ban
a user with:

```
:room ban @user:example.com
```

If you would like to unban someone, you can do:

```
:room unban @user:example.com
```

And if you just need to kick them out of the room without banning them (for
example, when dealing with a user from a homeserver that no longer exists and
is causing perpetual errors in federation), then you can do:

```
:room kick @user:example.com
```

If you find yourself managing a large room and needing to often ban users, you
may want to look at something like [mjolnir] to help you manage a ban list.

## Setting Room Aliases

You can add a new alias to a room with:

```
:room alias set #alias:example.com
```

And remove an alias with:

```
:room alias unset #alias:example.com
```

If you want to add a canonical alias or promote an existing one to be
canonical, then you can use:

```
:room canon set #alias:example.com
```

If there was an existing canonical alias, then it will be demoted to a regular
alternative room alias.

If you want a room alias to no longer be canonical, then you can make it an
alternative alias with:

```
:room canon unset #alias:example.com
```

> If you don't know what the room's current canonical or alternative aliases
> are, you can see them with:
>
> ```
> :room canon show
> :room alias show
> ```

## Setting Room Properties

You can set the description of the currently focused room using its `set` command:

```
:room topic set "This is the new room topic"
```

Similarly, if you need to change the room's name:

```
:room name set "Watercooler Discussion"
```

If you want to remove the topic or name, you can use `:room topic unset` or
`:room name unset`.

## Setting History Visibility

Depending on what your rooms are used for, you may want to configure different
visibility settings for the room history. Your options include:

- `invited`, which configures the room to allow people to see history from the point they were invited onwards.
-  `joined`, which configures the room to allow people to see history from the point they actually join the room.
-  `shared`, which configures the room to allow people to see all history once they are joined, including messages from before they joined.
-  `world`/`world_readable` which configures the room to allow anyone to see the room history regardless of whether they are joined and in it.

You can then set it with:

```
:room history set [invited|joined|shared|world]
```

You can see the current setting with:

```
:room history show
```

[mjolnir]: https://github.com/matrix-org/mjolnir
