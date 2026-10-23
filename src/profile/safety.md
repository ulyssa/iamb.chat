# Privacy And Safety

## Ignoring Users

If you need to ignore a user who is spamming a room, harassing you, or otherwise
causing you difficulty, you can ignore them with:

```
:ignore set @user:example.com
```

To see the users who you currently have ignored on your accont, then you can run:

```
:ignore show
```

If you change your mind or accidentally blocked the wrong user identifier, you
can run:

```
:ignore unset @user:example.com
```

## Auto-Rejecting Invites

If you are continuously receiving spam invites to rooms and unwanted direct
messages, you can enable auto-rejecting all invitations with:

```
:self invites set block
```

To view the current state for your account's settings:

```
:self invites show
```

To restore it, you can run one of:

```
:self invites set allow
:self invites unset
```
