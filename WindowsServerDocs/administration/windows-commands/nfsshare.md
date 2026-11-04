---
layout: Conceptual
title: nfsshare | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nfsshare
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nfsshare command, which controls Network File System (NFS) shares.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: cfe375dd-ff77-48b4-3111-4da6bb285953
document_version_independent_id: fd02b968-3060-0b17-1b04-9a60f348ba9c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nfsshare.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nfsshare
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nfsshare.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: d6ea5f8c-d40a-a563-3c59-f727ea8db17c
---

# nfsshare | Microsoft Learn

Controls Network File System (NFS) shares. Used without parameters, this command displays all Network File System (NFS) shares exported by Server for NFS.

## Syntax

```
nfsshare <sharename>=<drive:path> [-o <option=value>...]
nfsshare {<sharename> | <drive>:<path> | * } /delete
```

### Parameters

| Parameter | Description |
| --- | --- |
| -o anon=`{yes|no}` | Specifies whether anonymous (unmapped) users can access the share directory. |
| -o rw=`[<host>[:<host>]...]` | Provides read-write access to the shared directory by the hosts or client groups specified by *host*. You must separate host and group names with a colon (**:**). If *host* isn't specified, all hosts and client groups (except those specified with the **ro** option) get read-write access. If neither the **ro** nor the **rw** option is set, all clients have read-write access to the shared directory. |
| -o ro=`[<host>[:<host>]...]` | Provides read-only access to the shared directory by the hosts or client groups specified by *host*. You must separate host and group names with a colon (**:**). If *host* isn't specified, all clients (except those specified with the **rw** option) get read-only access. If the **ro** option is set for one or more clients, but the **rw** option isn't set, only the clients specified with the **ro** option have access to the shared directory. |
| -o encoding=`{euc-jp|euc-tw|euc-kr|shift-jis|Big5|Ksc5601|Gb2312-80|Ansi)` | Specifies the language encoding to configure on an NFS share. You can use only one language on the share. This value can include any of the following values:<br>- **euc-jp:** Japanese<br>- **euc-tw:** Chinese<br>- **euc-kr:** Korean<br>- **shift-jis:** Japanese<br>- **Big5:** Chinese<br>- **Ksc5601:** Korean<br>- **Gb2312-80:** Simplified Chinese<br>- **Ansi:** ANSI-encoded |
| -o anongid=`<gid>` | Specifies that anonymous (unmapped) users access the share directory using *gid* as their group identifier (GID). The default is **-2**. The anonymous GID is used when reporting the owner of a file owned by an unmapped user, even if anonymous access is disabled. |
| -o anonuid=`<uid>` | Specifies that anonymous (unmapped) users access the share directory using *uid* as their user identifier (UID). The default is **-2**. The anonymous UID is used when reporting the owner of a file owned by an unmapped user, even if anonymous access is disabled. |
| -o root=`[<host>[:<host>]...]` | Provides root access to the shared directory by the hosts or client groups specified by *host*. You must separate host and group names with a colon (**:**). If *host* isn't specified, all clients get root access. If the **root** option isn't set, no clients have root access to the shared directory. |
| /delete | If *sharename* or `<drive>:<path>` is specified, this parameter deletes the specified share. If a wildcard (\*) is specified, this parameter deletes all NFS shares. |
| /? | Displays help at the command prompt. |

#### Remarks

- If *sharename* as the only parameter, this command lists the properties of the NFS share identified by *sharename*.
- If *sharename* and `<drive>:<path>` are used, this command exports the folder identified by `<drive>:<path>` as *sharename*. If you use the **/delete** option, the specified folder stops being available to NFS clients.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Services for Network File System Command Reference](services-for-network-file-system-command-reference)
- [NFS cmdlets reference](/en-us/powershell/module/nfs)