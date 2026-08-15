# Command Reference

## iamb commands

### General Commands

| Command                 | Aliases                               | Help                                                |
| -------------------     | ------------------------------------- | -----------------------------------------           |
| `:chats`                |                                       | See [Browsing Rooms And DMs Together]               |
| `:create`               |                                       | See [Room Creation]                                 |
| `:dms`                  |                                       | See [Browsing Direct Messages]                      |
| `:forget`               |                                       | See [Joining And Leaving Rooms]                     |
| `:join`                 |                                       | See [Joining And Leaving Rooms]                     |
| `:keys export`          |                                       | See [Exporting / Importing Keys]                    |
| `:keys import`          |                                       | See [Exporting / Importing Keys]                    |
| `:logout`               |                                       | Log out of the client.                              |
| `:members`              |                                       | See [Viewing Room/Space Members]                    |
| `:rooms`                |                                       | See [Browsing Rooms]                                |
| `:spaces`               |                                       | See [Browsing Spaces]                               |
| `:unreads`              |                                       | See [Browsing Unreads]                              |
| `:unreads clear`        |                                       | See [Browsing Unreads]                              |
| `:verify`               |                                       | See [Verification]                                  |
| `:welcome`              |                                       | Shows the startup Welcome window                    |

### Message Commands

The following commands target the currently selected message, or allow
sending new ones:

| Command                 | Aliases                               | Help                                                |
| -------------------     | ------------------------------------- | -----------------------------------------           |
| `:download`             |                                       | See [Downloading Attachments]                       |
| `:edit`                 |                                       | See [Editing Messages]                              |
| `:editor`               |                                       | See [Sending]                                       |
| `:open`                 |                                       | See [Downloading Attachments] and [Opening Links]   |
| `:react`                |                                       | See [Reacting To A Message]                         |
| `:redact`               |                                       | See [Redacting A Message]                           |
| `:replied`              |                                       | See [Replying To A Message]                         |
| `:reply`                |                                       | See [Replying To A Message]                         |
| `:unreact`              |                                       | See [Reacting To A Message]                         |
| `:upload`               |                                       | See [Uploads]                                       |

### Room Commands

The following commands target the currently selected room
(including spaces, which are just a special kind of room):

| Command                 | Aliases                               | Help                                                |
| -------------------     | ------------------------------------- | -----------------------------------------           |
| `:invite accept`        |                                       | See [Room Invitations]                              |
| `:invite reject`        |                                       | See [Room Invitations]                              |
| `:invite send`          |                                       | See [Room Invitations]                              |
| `:leave`                |                                       | See [Joining And Leaving Rooms]                     |
| `:room alias set`       |                                       | See [Setting Room Aliases]                          |
| `:room alias show`      |                                       | See [Setting Room Aliases]                          |
| `:room alias unset`     |                                       | See [Setting Room Aliases]                          |
| `:room ban`             |                                       | See [Managing Room Membership]                      |
| `:room canon set`       | `:room canonicalalias set`            | See [Setting Room Aliases]                          |
| `:room canon show`      | `:room canonicalalias show`           | See [Setting Room Aliases]                          |
| `:room canon unset`     | `:room canonicalalias unset`          | See [Setting Room Aliases]                          |
| `:room dm unset`        |                                       | See [Marking Direct Rooms]                          |
| `:room dm set`          |                                       | See [Marking Direct Rooms]                          |
| `:room dm unset`        |                                       | See [Marking Direct Rooms]                          |
| `:room history set`     |                                       | See [Setting History Visibility]                    |
| `:room history unset`   |                                       | See [Setting History Visibility]                    |
| `:room id show`         |                                       | See [Updating Space Hierarchy]                      |
| `:room kick`            |                                       | See [Managing Room Membership]                      |
| `:room name set`        |                                       | See [Setting Room Properties]                       |
| `:room name show`       |                                       | See [Setting Room Properties]                       |
| `:room name unset`      |                                       | See [Setting Room Properties]                       |
| `:room notify set`      |                                       | See [Configuring Room Notifications]                |
| `:room notify show`     |                                       | See [Configuring Room Notifications]                |
| `:room notify unset`    |                                       | See [Configuring Room Notifications]                |
| `:room tag set`         |                                       | See [Setting Room Tags]                             |
| `:room tag unset`       |                                       | See [Setting Room Tags]                             |
| `:room topic set`       |                                       | See [Setting Room Properties]                       |
| `:room topic show`      |                                       | See [Setting Room Properties]                       |
| `:room topic unset`     |                                       | See [Setting Room Properties]                       |
| `:room unban`           |                                       | See [Managing Room Membership]                      |
| `:space child remove`   |                                       | See [Updating Space Hierarchy]                      |
| `:space child set`      |                                       | See [Updating Space Hierarchy]                      |

## Vim commands

| Command         | Aliases                               | Help                                |
| --------------- | ------------------------------------- | ----------------------------------- |
| `:close`        | `:clo`                                | See [Closing Windows]               |
| `:horizontal`   | `:hor`                                | See [Opening Windows]               |
| `:leftabove`    | `:lefta`, `:aboveleft`, `:abo`        | See [Opening Windows]               |
| `:only`         | `:on`                                 | See [Closing Windows]               |
| `:quitall`      | `:qa`, `:qall`, `:quita`              | See [Closing Windows]               |
| `:quit`         | `:q`                                  | See [Closing Windows]               |
| `:resize`       |                                       | See [Resizing Windows]              |
| `:rightbelow`   | `:rightb`, `:belowright`, `:bel`      | See [Opening Windows]               |
| `:split`        | `:sp`                                 | See [Opening Windows]               |
| `:tab`          |                                       | See [Opening Tabs]                  |
| `:tabclose`     | `:tabc`                               | See [Closing Tabs]                  |
| `:tabedit`      | `:tabe`, `:tabnew`                    | See [Opening Tabs]                  |
| `:tablast`      | `:tabl`                               | See [Switching Tabs]                |
| `:tabmove`      | `:tabm`                               | See [Organizing Tabs]               |
| `:tabnext`      | `:tabn`                               | See [Switching Tabs]                |
| `:tabonly`      | `:tabo`                               | See [Closing Tabs]                  |
| `:tabprevious`  | `:tabp`, `:tabNext`, `:tabN`          | See [Switching Tabs]                |
| `:tabrewind`    | `:tabr`, `:tabfirst`, `:tabfir`       | See [Switching Tabs]                |
| `:vertical`     | `:vert`                               | See [Opening Windows]               |
| `:vsplit`       | `:vs`, `:vsp`                         | See [Opening Windows]               |

<style>
table {
    width: 100%;
}
table th:first-of-type {
    width: 30%;
}
table th:nth-of-type(2) {
    width: 25%;
}
table th:nth-of-type(3) {
    width: 45%;
}
</style>

[Browsing Direct Messages]: ./rooms/browsing.md#browsing-direct-messages
[Browsing Rooms]: ./rooms/browsing.md#browsing-rooms
[Browsing Rooms And DMs Together]: ./rooms/browsing.md#browsing-rooms-and-dms-together
[Browsing Spaces]: ./rooms/browsing.md#browsing-spaces
[Browsing Unreads]: ./rooms/browsing.md#browsing-unreads
[Closing Tabs]: ./layout/tabs.md#closing-tabs
[Closing Windows]: ./layout/tabs.md#closing-windows
[Configuring Room Notifications]: ./rooms/management.md#configuring-room-notifications
[Downloading Attachments]: ./messages/#downloading-attachments
[Editing Messages]: ./messages/#editing-messages
[Exporting / Importing Keys]: ./e2ee/keys.md#exporting-importing-keys
[Managing Room Membership]: ./rooms/admin.md#managing-room-membership
[Marking Direct Rooms]: ./rooms/management.md#marking-direct-rooms
[Opening Links]: ./messages/#opening-links
[Opening Tabs]: ./layout/tabs.md#opening-tabs
[Opening Windows]: ./layout/windows.md#opening-windows
[Organizing Tabs]: ./layout/tabs.md#organizing-tabs
[Reacting To A Message]: ./messages/#reacting-to-a-message
[Redacting A Message]: ./messages/#redacting-a-message
[Replying To A Message]: ./messages/#replying-to-a-message
[Resizing Windows]: ./layout/windows.md#resizing-windows
[Room Creation]: ./rooms/management.md#room-creation
[Room Invitations]: ./rooms/management.md#room-invitations
[Updating Space Hierarchy]: ../rooms/admin.md#updating-space-hierarchy
[Joining And Leaving Rooms]: ./rooms/#joining-and-leaving-rooms
[Sending]: ./messages/#sending
[Setting History Visibility]: ./rooms/admin.md#setting-history-visibility
[Setting Room Aliases]: ./rooms/admin.md#setting-room-aliases
[Setting Room Properties]: ./rooms/admin.md#setting-room-properties
[Setting Room Tags]: ./rooms/management.md#setting-room-tags
[Switching Tabs]: ./layout/tabs.md#switching-tabs
[Uploads]: ./messages/#uploads
[Verification]: ./e2ee/verify.md
[Viewing Room/Space Members]: ./rooms/members.md#viewing-roomspace-members
