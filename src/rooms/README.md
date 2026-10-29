# Rooms

## Joining And Leaving Rooms or Direct Messages

You can join a new room, space or direct message using the `:join` command. For example, to
join the Matrix community space, you can run:

```
:join #community:matrix.org
```

You can similarly start a new direct message and **iamb** will automatically handle the user invite:

```
:join @user:example.com
```

You can leave the currently focused room via the `:leave` command. This will
prompt for confirmation by default, but you can override it by appending `!`:

```
:leave!
```

To remove all left rooms from local client state and database, use the `:forget` command:

```
:forget
```
