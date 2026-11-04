---
layout: Conceptual
title: openfiles | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/openfiles
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the openfiles command, which enables an administrator to query, display, or disconnect files and directories that have been opened on a system.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a1b5e5c4-7a92-e16f-9221-a5f2c94ce9c3
document_version_independent_id: 37853f4f-d203-fef6-2f5d-f6a740f7afbe
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/openfiles.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/openfiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/openfiles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4b6a54af-41c1-e93b-ddea-dcfdaff092e3
---

# openfiles | Microsoft Learn

Enables an administrator to query, display, or disconnect files and directories that have been opened on a system. This command also enables or disables the system **Maintain Objects List** global flag.

## openfiles /disconnect

Enables an administrator to disconnect files and folders that have been opened remotely through a shared folder.

### Syntax

```
openfiles /disconnect [/s <system> [/u [<domain>\]<username> [/p [<password>]]]] {[/id <openfileID>] | [/a <accessedby>] | [/o {read | write | read/write}]} [/op <openfile>]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| /s `<system>` | Specifies the remote system to connect to (by name or IP address). Don't use backslashes. If you don't use the **/s** option, the command is run on the local computer by default. This parameter applies to all files and folders that are specified in the command. |
| /u `[<domain>\]<username>` | Runs the command using the permissions of the specified user account. If you don't use the **/u** option, system permissions are used by default. |
| /p `[<password>]` | Specifies the password of the user account that is specified in the **/u** option. If you don't use the **/p** option, a password prompt appears when the command is run. |
| /id `<openfileID>` | Disconnects open files by the specified file ID. You can use the wildcard character (**\***) with this parameter.<br>Note: You can use the **openfiles /query** command to find the file ID. |
| /a `<accessedby>` | Disconnects all open files associated with the user name specified in the *accessedby* parameter. You can use the wildcard character (**\***) with this parameter. |
| /o `{read | write | read/write}` | Disconnects all open files with the specified open mode value. Valid values are **Read**, **Write**, or **Read/Write**. You can use the wildcard character (**\***) with this parameter. |
| /op `<openfile>` | Disconnects all open file connections that are created by a specific open file name. You can use the wildcard character (**\***) with this parameter. |
| /? | Displays help at the command prompt. |

### Examples

To disconnect all open files with the *file ID 26843578*, type:

```
openfiles /disconnect /id 26843578
```

To disconnect all open files and directories accessed by the user *hiropln*, type:

```
openfiles /disconnect /a hiropln
```

To disconnect all open files and directories with *read/write mode*, type:

```
openfiles /disconnect /o read/write
```

To disconnect the directory with the open file name \*C:\testshare\*, regardless of who is accessing it, type:

```
openfiles /disconnect /a * /op c:\testshare\
```

To disconnect all open files on the remote computer *srvmain* that are being accessed by the user *hiropln*, regardless of their ID, type:

```
openfiles /disconnect /s srvmain /u maindom\hiropln /id *
```

## openfiles /query

Queries and displays all open files.

### Syntax

```
openfiles /query [/s <system> [/u [<domain>\]<username> [/p [<password>]]]] [/fo {TABLE | LIST | CSV}] [/nh] [/v]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| /s `<system>` | Specifies the remote system to connect to (by name or IP address). Don't use backslashes. If you don't use the **/s** option, the command is run on the local computer by default. This parameter applies to all files and folders that are specified in the command. |
| /u `[<domain>\]<username>` | Runs the command using the permissions of the specified user account. If you don't use the **/u** option, system permissions are used by default. |
| /p `[<password>]` | Specifies the password of the user account that is specified in the **/u** option. If you don't use the **/p** option, a password prompt appears when the command is run. |
| [/fo `{TABLE | LIST | CSV}`] | Displays the output in the specified format. Valid values include:<br>- **TABLE** - Displays output in a table.<br>- **LIST** - Displays output in a list.<br>- **CSV** - Displays output in Comma Separated Values (CSV) format. |
| /nh | Suppresses column headers in the output. Valid only when the **/fo** parameter is set to **TABLE** or **CSV**. |
| /v | Specifies that detailed (verbose) information be displayed in the output. |
| /? | Displays help at the command prompt. |

### Examples

To query and display all open files, type:

```
openfiles /query
```

To query and display all open files in table format without headers, type:

```
openfiles /query /fo table /nh
```

To query and display all open files in list format with detailed information, type:

```
openfiles /query /fo list /v
```

To query and display all open files on the remote system *srvmain* by using the credentials for the user *hiropln* on the *maindom* domain, type:

```
openfiles /query /s srvmain /u maindom\hiropln /p p@ssW23
```

Note

In this example, the password is supplied on the command line. To prevent displaying the password, leave out the **/p** option. You'll be prompted for the password, which won't be echoed to the screen.

## openfiles /local

Enables or disables the system **Maintain Objects List** global flag. If used without parameters, **openfiles /local** displays the current status of the **Maintain Objects List** global flag.

Note

Changes made by using the **on** or **off** option don't take effect until you restart the system. Enabling the **Maintain Objects List** global flag might slow down your system.

### Syntax

```
openfiles /local [on | off]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| `[on | off]` | Enables or disables the system **Maintain Objects List** global flag, which tracks local file handles. |
| /? | Displays help at the command prompt. |

### Examples

To check the current status of the **Maintain Objects List** global flag, type:

```
openfiles /local
```

By default, the **Maintain Objects List** global flag is disabled, and the following message appears, `INFO: The system global flag 'maintain objects list' is currently disabled.`

To enable the **Maintain Objects List** global flag, type:

```
openfiles /local on
```

The following message appears when the global flag is enabled, `SUCCESS: The system global flag 'maintain objects list' is enabled. This will take effect after the system is restarted.`

To disable the **Maintain Objects List** global flag, type:

```
openfiles /local off
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)