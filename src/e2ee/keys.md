# Room Keys

## Exporting / Importing Keys

If you want to export your room keys, either to save them as a backup or
to import them into another session, you can use:

```
:keys export /path/to/output.keys passphrase
``` 

This will write out the keys encrypted with the given passphrase.

When you have keys that you would like to import into __iamb__, you can do so
with:

```
:keys import /path/to/input.keys passphrase
```
