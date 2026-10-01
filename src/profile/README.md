# User Profile

## Display Name

You can set your display name with:

```
:self name set "John Doe"
```

> 💡 You can set a per-room display name using `:room user name set`, which
> will update your membership state event in just that room. Note that future
> calls to `:self name set` will update your name in *all* rooms, overwriting
> any previously set values.

To see your current display name:

```
:self name show
```

If you then want to clear your display name:

```
:self name unset
```

## User Avatar

You can set the `mxc://` URL for your avatar with:

```
:self avatar set
```

To see your current avatar URL:

```
:self avatar show
```

If you then want to clear the value:

```
:self avatar unset
```

## Timezone

On homeservers that support it, you can indicate your timezone with:

```
:self timezone set "Europe/Paris"
```

To see your current timezone:

```
:self timezone show
```

If you then want to clear the value:

```
:self timezone unset
```
