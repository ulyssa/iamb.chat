# End-To-End Encryption

__iamb__ supports End-To-End Encryption (E2EE) for Matrix rooms.

## Encryption Status Indicator

When viewing a room window, the encryption state of the room is indicated in
the prompt of the message bar:

- Green <code style="color: green">[E]</code> indicates that the room is **encrypted**.
- Red <code style="color: red">[U]</code> indicates that the room is **unencrypted**.
- Yellow <code style="color: yellow">[?]</code> indicates that the room's encryption state is **unknown**.

Note that these are colored using the ANSI colors in the `default` theme, so depending
on your terminal colors they may appear differently.

Most of the themes made for __iamb__ try to find shades of these colors for you
to use, but some might drift a little. Notably, if you are colorblind and find
it hard to distinguish between green and red, then you may wish to use the
`okabe-ito-dark` theme, which uses
a blue <code style="color: #0072B2">[E]</code>,
orange <code style="color: #D55E00">[U]</code>, and
yellow <code style="color: #F0E442">[?]</code>.
